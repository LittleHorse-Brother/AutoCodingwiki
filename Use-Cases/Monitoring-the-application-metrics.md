# Add metrics monitoring to your application

1. Add a reference `Comm100.Metrics` in your project. Please use the latest version.
![image.png](/.attachments/image-274bf5cf-2a69-4f32-b194-af52c25bba3a.png)

2. Add the required metrics and interfaces to your code

  - Add Runtime counter metrics
 ![image.png](/.attachments/image-876a2cad-bdb5-4e10-9bc2-c8a4b359ec2f.png)

  - Add Http Metrics monitoring middleware & the metrics endpoint
![image.png](/.attachments/image-f88854e0-6145-4b26-aa59-c3ecf7cab233.png)

3. Run the application to check whether the metrics endpoint is work.

   Access the `/metrics` endpoint and you will get the following results.
![image.png](/.attachments/image-8106ee2e-277e-4725-acfa-1d32cf8945d0.png)


# Let Prometheus to scrape the application metrics

1. Publish  your application to the testing 

2. Let the devops person add a label (`prometheus.io/scrape: 'true'`) to your service so that the Prometheus will scrape the metrics.

  - For testing environment, you can add label by yourself
![image.png](/.attachments/image-90ba3d57-7139-428d-8a2f-8c3b34bfbf4f.png)

3. Consult the Devops team for more Prometheus configurations.


# View monitoring metrics in Grafana

1. Access Grafana in the testing environment

  - https://monitor.testing.comm100dev.io/

2. Import the following dashboard

  - Dotnet Runtime Dashboard 
  [dotnet-runtime-dashboard.json](/.attachments/dotnet-runtime-dashboard-359fbce6-d867-4ab2-b059-6b4c8e7e12f4.json)

  - Dotnet Http & Other 
  [net-http-regular-dashboard.json](/.attachments/net-http-regular-dashboard-65bafc53-fea1-46f7-87b2-6da179ef3bab.json)

3. View Dashboard
  - Dotnet Runtime Dashboard
![image.png](/.attachments/image-b7657bff-1414-482e-a3da-baa2ed3bc80f.png)
  - Dotnet Http & Other
![image.png](/.attachments/image-b13e5e3e-6d93-4e4d-aa63-f8b2c01f8a32.png)

# Meaning of the metrics


## Dotnet core


### GC

#### dotnet_gc_memory_total_available_bytes

  The upper limit on the amount of physical memory .NET can allocate to

  - `type`: gauge

    ```
      dotnet_gc_memory_total_available_bytes 157286400
    ```

#### dotnet_gc_pause_ratio

  The percentage of time the process spent paused for garbage collection

  - `type`: gauge

    ```
      dotnet_gc_pause_ratio 0
    ```

#### dotnet_gc_collection_count_total

  Counts the number of garbage collections that have occurred, broken down by generation number.

  - `type`: counter

    ```
      dotnet_gc_collection_count_total{gc_generation="1"} 787
      dotnet_gc_collection_count_total{gc_generation="2"} 37
      dotnet_gc_collection_count_total{gc_generation="0"} 3619
    ```

#### dotnet_gc_heap_size_bytes

  The current size of all heaps (only updated after a garbage collection)

  - `type`: gauge

    ```
      dotnet_gc_heap_size_bytes{gc_generation="1"} 301616
      dotnet_gc_heap_size_bytes{gc_generation="loh"} 860912
      dotnet_gc_heap_size_bytes{gc_generation="2"} 12276744
      dotnet_gc_heap_size_bytes{gc_generation="0"} 24
    ```

#### dotnet_gc_allocated_bytes_total

  The total number of bytes allocated on the managed heap

  - `type`: counter

    ```
      dotnet_gc_allocated_bytes_total 60605352504
    ```

### Thread Pool

#### dotnet_threadpool_queue_length 

  Measures the queue length of the thread pool. Values greater than 0 indicate a backlog of work for the threadpool to process.

  - `type`: histogram

    ```
      dotnet_threadpool_queue_length_sum 5628
      dotnet_threadpool_queue_length_count 415818
      dotnet_threadpool_queue_length_bucket{le="0"} 412675
      dotnet_threadpool_queue_length_bucket{le="1"} 413843
      dotnet_threadpool_queue_length_bucket{le="10"} 415818
      dotnet_threadpool_queue_length_bucket{le="100"} 415818
      dotnet_threadpool_queue_length_bucket{le="1000"} 415818
      dotnet_threadpool_queue_length_bucket{le="+Inf"} 415818
    ```


#### dotnet_threadpool_num_threads 

  The number of active threads in the thread pool

  - `type`: gauge

    ```
      dotnet_threadpool_num_threads 1
    ```

#### dotnet_threadpool_timer_count 

  The number of timers active
  - `type`: gauge

    ```
      dotnet_threadpool_timer_count 8
    ```

#### process_cpu_count 

  The number of processor cores available to this process.

  - `type`: gauge

    ```
      process_cpu_count 1
    ```

#### dotnet_threadpool_throughput_total 

  The total number of work items that have finished execution in the thread pool

  - `type`: counter

    ```
      dotnet_threadpool_throughput_total 3125187
    ```


### SQL Client

#### dotnet_sqlclient_number_of_stasis_connections

  Number of connections currently waiting to be ready

  - `type`: gauge

    ```
      dotnet_sqlclient_number_of_stasis_connections 0
    ```

#### dotnet_sqlclient_number_of_inactive_connection_pools

  Number of inactive connection pools

  - `type`: gauge

    ```
      dotnet_sqlclient_number_of_inactive_connection_pools 0
    ```

#### dotnet_sqlclient_number_of_active_connections

  Number of active connections

  - `type`: gauge

    ```
      dotnet_sqlclient_number_of_active_connections 0
    ```

#### dotnet_sqlclient_soft_connects

  Number of connections we get from the pool

  - `type`: counter

    ```
      dotnet_sqlclient_soft_connects 4
    ```

#### dotnet_sqlclient_number_of_free_connections

  Number of ready connections in the connection pool

  - `type`: gauge

    ```
      dotnet_sqlclient_number_of_free_connections 1
    ```

#### dotnet_sqlclient_soft_disconnects

  Number of connections we return to the pool

  - `type`: counter

    ```
      dotnet_sqlclient_soft_disconnects 4
    ```

#### dotnet_sqlclient_number_of_active_connection_pools

  Number of active connection pools

  - `type`: gauge

    ```
      dotnet_sqlclient_number_of_active_connection_pools 1
    ```

#### dotnet_sqlclient_number_of_reclaimed_connections

  Number of reclaimed connections from GC

  - `type`: counter

    ```
      dotnet_sqlclient_number_of_reclaimed_connections 0
    ```

#### dotnet_sqlclient_number_of_non_pooled_connections

  Number of connections that are not using connection pooling

  - `type`: gauge

    ```
      dotnet_sqlclient_number_of_non_pooled_connections 0
    ```

#### dotnet_sqlclient_hard_disconnects

  Number of actual disconnects that are being made to servers

  - `type`: counter

    ```
      dotnet_sqlclient_hard_disconnects 0
    ```

#### dotnet_sqlclient_active_hard_connections

  Number of actual active connections that are being made to servers

  - `type`: gauge

    ```
      dotnet_sqlclient_active_hard_connections 1
    ```

#### dotnet_sqlclient_hard_connects

  Number of actual connection that are being made to servers

  - `type`: counter

    ```
      dotnet_sqlclient_hard_connects 1
    ```

#### dotnet_sqlclient_number_of_pooled_connections

  Number of connections that are managed by the connection pool

  - `type`: gauge

    ```
      dotnet_sqlclient_number_of_pooled_connections 1
    ```

#### dotnet_sqlclient_number_of_inactive_connection_pool_groups

  Number of unique connection strings waiting for pruning

  - `type`: gauge

    ```
      dotnet_sqlclient_number_of_inactive_connection_pool_groups 0
    ```

#### dotnet_sqlclient_number_of_active_connection_pool_groups

  Number of active unique connection strings

  - `type`: gauge

    ```
      dotnet_sqlclient_number_of_active_connection_pool_groups 1
    ```

#### dotnet_sqlclient_active_soft_connects

  Number of active pool connections

  - `type`: gauge

    ```
      dotnet_sqlclient_active_soft_connects 0
    ```


### Contention & Exception 

#### dotnet_contention_total

  The number of locks contended

  - `type`: counter

    ```
      dotnet_contention_total 12496
    ```


#### dotnet_exceptions_total 

  Count of exceptions thrown

  - `type`: counter

    ```
      dotnet_exceptions_total 136
    ```


## CPU & Process

### process_cpu_seconds_total
  
  Total user and system CPU time spent in seconds.
  
  - `type`: counter

    ```
      process_cpu_seconds_total 363.71
    ```

### process_start_time_seconds
  
  Start time of the process since unix epoch in seconds.
  
  - `type`: gauge

    ```
      process_start_time_seconds 1635833110.6
    ```

### process_open_handles 
  
  Number of open handles
  
  - `type`: gauge

    ```
      process_open_handles 259
    ```

### process_num_threads
  
  Total number of threads
  
  - `type`: gauge

    ```
      process_num_threads 17
    ```

## Memory

### dotnet_total_memory_bytes

  Total known allocated memory
  
  - `type`: gauge

    ```
      dotnet_total_memory_bytes 21839032
    ```

## process_virtual_memory_bytes 
  
  Virtual memory size in bytes.
  
  - `type`: gauge

    ```
      process_virtual_memory_bytes 4417527808
    ```

## process_private_memory_bytes 
  
  Process private memory size
  
  - `type`: gauge

    ```
      process_private_memory_bytes 259948544
    ```

### process_working_set_bytes
  Process working set
  
  - `type`: gauge

    ```
      process_working_set_bytes 183209984
    ```

## Http Request

### http_requests_in_progress
  
  The number of requests currently in progress in the ASP.NET Core pipeline. One series without controller/action label values counts all in-progress requests, with separate series existing for each controller-action pair.
  
  - `type`: gauge

    ```
      http_requests_in_progress{method="GET",controller="Cubes",action="GetCubeList"} 0
      http_requests_in_progress{method="POST",controller="Reports",action="Query"} 0
    ```

### http_requests_received_total
  
  Provides the count of HTTP requests that have been processed by the ASP.NET Core pipeline.
  
  - `type`: counter

    ```
      http_requests_received_total{code="200",method="POST",controller="Reports",action="Query"} 235
      http_requests_received_total{code="200",method="GET",controller="Cubes",action="GetCubeList"} 3
    ```

### http_request_duration_seconds 
  The duration of HTTP requests processed by an ASP.NET Core application.
  
  - `type`: histogram

    ```
      http_request_duration_seconds_sum{code="200",method="POST",controller="Reports",action="Query"} 168.0948615
      http_request_duration_seconds_count{code="200",method="POST",controller="Reports",action="Query"} 235
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.001"} 0
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.002"} 0
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.004"} 0
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.008"} 0
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.016"} 0
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.032"} 32
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.064"} 56
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.128"} 85
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.256"} 105
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="0.512"} 123
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="1.024"} 187
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="2.048"} 225
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="4.096"} 232
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="8.192"} 234
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="16.384"} 234
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="32.768"} 235
      http_request_duration_seconds_bucket{code="200",method="POST",controller="Reports",action="Query",le="+Inf"} 235
      http_request_duration_seconds_sum{code="200",method="GET",controller="Cubes",action="GetCubeList"} 1.3646032999999997
      http_request_duration_seconds_count{code="200",method="GET",controller="Cubes",action="GetCubeList"} 3
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.001"} 0
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.002"} 0
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.004"} 0
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.008"} 1
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.016"} 2
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.032"} 2
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.064"} 2
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.128"} 2
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.256"} 2
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="0.512"} 2
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="1.024"} 2
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="2.048"} 3
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="4.096"} 3
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="8.192"} 3
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="16.384"} 3
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="32.768"} 3
      http_request_duration_seconds_bucket{code="200",method="GET",controller="Cubes",action="GetCubeList",le="+Inf"} 3
    ```
    