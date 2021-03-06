# Load Testing and Tuning Kafka on DC/OS

The purpose of this guide is to teach users methods of how to tune the performance of Kafka running on DC/OS for goals of throughput, latency, availability, and durability using guidelines and best-practices provided by Confluent

See [Optimizing Your Apache Kafka Deployment](https://www.confluent.io/white-paper/optimizing-your-apache-kafka-deployment/) for the full whitepaper discussing how to optimize your Apache Kafka deployment for various service goals.

This guide was made using the Confluent-Kafka DC/OS Certified Framework, but all commands should work if you replace `confluent-kafka` references with just `kafka`

## [Load Testing Kafka Quickstart](https://github.com/ably77/DCOS-Kafka-Performance/blob/master/Quickstart.md)
- A quick guide that will teach the basics of performance testing tools available in the Kafka distribution. 
	- Requires 5 Nodes minimum (1x master, 4x agents)

## [Advanced Load Testing Kafka](https://github.com/ably77/DCOS-Kafka-Performance/blob/master/AdvancedTuning.md)
- A deep-dive guide to performance testing and scaling your Kafka cluster on DC/OS. More focused on high throughput, but advice is offered for balancing goals of throughput, latency, availability, and durability
	- Requires 6 nodes minimum (1x master, 4x Kafka agents, 1x Producer Agent)
	- Optional: Test options scale up to 36 nodes maximum (1x master, 10x Kafka Agents, 25 Producer Agents)

## Results:

Highest Single Producer Throughput: 
```
717360.114778 records/sec (171.03 MB/sec), 8.83 ms avg latency, 226.00 ms max latency
```

6x Kafka Broker // 3 Producer Aggregate Throughput:
```
2191825.22 records/sec, 522.57 MB/sec, 9.34 ms avg latency, 225.33 ms avg max latency
```

6x Kafka Broker // 5 Producer Aggregate Throughput: 
```
3625119.68 records/sec, 864.3 MB/sec, 10.34 ms avg latency, 231.4 ms avg max latency
```

6x Kafka Broker // 10 Producer Aggregate Throughput: 
```
7212422.22 records/sec, 1719.57 MB/sec, 12.52 ms avg latency, 228.8 ms avg max latency
```

6x Kafka Broker // 15 Producer Aggregate Throughput: 
```
10556400.74 records/sec, 2516.83 MB/sec, 54.86 ms avg latency, 336.53 ms avg max latency
```

9x Kafka Broker // 25 Producer Aggregate Throughput: 
```
16254111.4 records/sec, 3875.3 MB/sec, 31.5768 ms avg latency, 437.24 ms avg max latency
```

## WIP:

A couple improvements can still be made to squeeze more overall performance from your Kafka deployment. Over time I will be adding more detailed information on how to:
- Use a dedicated Kafka-Zookeeper in conjunction with the Kafka Framework
- Isolate disk I/O using `MOUNT` disks
- Maxing out I/O of the attached storage
- Increase JVM heap size
- Testing more storage/networking optimized instances other than m3.xlarge (i.e. r3, h1, i3, and d2 instances in AWS)
- Balancing high throughput in exchange for a balanced profile of characteristics (durability, latency, availability)
