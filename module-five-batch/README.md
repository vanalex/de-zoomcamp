### Question 1

```python
import pyspark
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .master("local[*]") \
    .appName('test') \
    .getOrCreate()

print(spark.version)
```

The output was 3.5.5

### Question 2

```python
df = spark.read.parquet("yellow_tripdata_2024-10.parquet")
df = df.repartition(4)
df.write.parquet('yellow/2024/10')
```

The parquet files were 22.4 mb each.


### Question 3

```python
from pyspark.sql.functions import col, to_date
df.filter(to_date(col("tpep_pickup_datetime")) == "2024-10-15") \
.count()
```

The output was 128893.


### Question4

```python
df.registerTempTable('trips_data')
spark.sql("""
select MAX(timestampdiff(HOUR, tpep_pickup_datetime, tpep_dropoff_datetime)) from trips_data
""").show()
```

The output was 162.


### Question 5

Spark UI is available at localhost:4040.



### Question 6

```python
zone = spark.read \
    .option("header", "true") \
    .csv('taxi_zone_lookup.csv')

from pyspark.sql.functions import col
zone = zone.withColumn("LocationID", col("LocationID").cast("int"))

zone.registerTempTable('zones')

spark.sql("""
select t2.Zone, count(*) as num_trips from trips_data t1 inner join zones t2 on t1.PULocationID = t2.LocationID
group by t2.Zone
order by num_trips
LIMIT 1
""").show(truncate=False)
```

The output shows "Governor's Island/Ellis Island/Liberty Island".