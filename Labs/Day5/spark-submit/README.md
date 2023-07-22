## How to run:
- Open Anaconda Prompt
- Set environment
```
D:
cd D:\22-Trngs\2-Confirmed\5-PySpark-56-hours-Geet
conda activate ./conda-env
cd D:\22-Trngs\2-Confirmed\5-PySpark-56-hours-Geet\GH\Labs\Day6\spark-submit
set PYSPARK_PYTHON=python
```

- Submit Spark Job
```
spark-submit hello.py --name "Sample Spark Application" spark-submit hello.py --name "Sample Spark Application"  --conf spark.eventLog.enabled=false --conf spark.sql.shuffle.partitions=2 --master local    --deploy-mode client --master local    --deploy-mode client
```
