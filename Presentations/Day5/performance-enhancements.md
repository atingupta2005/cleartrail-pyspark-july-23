## Indirect Performance Enhancements
### Design Choices
- Scala versus Java versus Python versus R
- DataFrames versus SQL versus Datasets versus RDDs

### Cluster Configurations
- Cluster/application sizing and sharing

### Dynamic allocation
- Spark provides a mechanism to dynamically adjust the resources your application occupies based on the workload. 
- This means that your application can give resources back to the cluster if they are no longer used, and request them again later when there is demand
- This feature is particularly useful if multiple applications share resources in your Spark cluster
- This feature is disabled by default
- If you’d like to enable this feature, you should set:
```
spark.dynamicAllocation.enabled to true
```

### Scheduling
- Setting --max-executor-cores, which specifies the maximum number of executor cores that your application will need.
- Specifying this value can ensure that your application does not take up all the resources on the cluster
- You can also change the default, depending on your cluster manager, by setting the configuration spark.cores.max to a default of your choice

### File-based long-term data storage
- Generally you should always favor structured, binary types to store your data, especially when you’ll be accessing it frequently.
- Although files like “CSV” seem well-structured, they’re very slow to parse

### Partitioning

### The number of files

### Shuffle Configurations

## Direct Performance Enhancements
### Parallelism
- The first thing you should do whenever trying to speed up a specific stage is to increase the degree of parallelism
- In general, we recommend having at least two or three tasks per CPU core in your cluster if the stage processes a large amount of data
- You can set this via the spark.default.parallelism property

### Improved Filtering
- Use Parque
- Enable Partitioning

### Chose Coalescing over Repartitioning

### Avoid using User-Defined Functions (UDFs)

### Use caching and use it only when absolutely required

### Brodcast Join vs Sort Merge Join
