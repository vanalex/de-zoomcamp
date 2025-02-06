## Homework answers

### Q1. Within the execution for Yellow Taxi data for the year 2020 and month 12: what is the uncompressed file size (i.e. the output file yellow_tripdata_2020-12.csv of the extract task)?

- Answer: 128.3 MB

### Q2. What is the value of the variable file when the inputs taxi is set to green, year is set to 2020, and month is set to 04 during execution?

- Answer: green_tripdata_2020-04.csv

### Q3. How many rows are there for the Yellow Taxi data for the year 2020?

```sh
    SELECT COUNT(*) AS row_count
    FROM yellow_tripdata
    WHERE filename LIKE 'yellow_tripdata_2020-%.csv'
```
- Answer: 24.648.499
  
### Q4. How many rows are there for the Green Taxi data for the year 2020?

```sh
  SELECT COUNT(*) AS row_count
  FROM green_tripdata
  WHERE filename LIKE 'green_tripdata_2020-%.csv'
```

- Answer: 1.734.051

### Q5. How many rows are there for the Yellow Taxi data for March 2021?

```sh
  SELECT COUNT(*) AS row_count
  FROM yellow_tripdata
  WHERE filename = 'yellow_tripdata_2021-03.csv'
```


- Answer: 1.925.152

### Q6. How would you configure the timezone to New York in a Schedule trigger?

- Answer: Add a timezone property set to America/New_York in the Schedule trigger configuration
