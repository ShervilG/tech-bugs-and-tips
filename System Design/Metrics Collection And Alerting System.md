#metrics #influxdb #systemdesign

# Overview
***
Here we need to create a system that can handle application infra level metrics such as RPM, CPU usage, RAM usage etc. We need aggregation on top of that and display it to some visualization tool.

# Basics
***
- Steps involve
	- Data Collection
	- Data Transmission
	- Data Storage
	- Data Visualization
	- Alerting
- We need a time series DB. InfluxDB is a good choice and can handle 250K writes per second on 8 core 32 gigs machine.
- Data Generally looks like this:
	- <metric-name, List<key:value> labels, List<timestamp:value> values> 
- These labels are also known as tags and DBs such as these provide good indexing based on these tags for efficient aggregation. 
	- E.g. -> <cpu_name : cpui123>, cpu_name is the label and cpuii123 is the identifier.
-  Data aggregation can happen either on client side, on the ingestion pipeline or at query level from the DB. The last one might increase the query time due to aggregation operations. Maintaining a counter on client side for aggregation can be a good option for some metrics. 

# Push vs Pull for Data Collection
***
- PULL Approach -> services expose some metric endpoint which the collection system calls periodically to collect data. This requires service discovery for metric system to identify where to pull data from. Easy to monitor pull services for errors since it's an API at their end which might be down.
- PUSH Approach -> services call APIs of Metric System to send it data. Cant tell if there's an issue with the services if they are not sending data.