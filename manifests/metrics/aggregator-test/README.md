# aggregator-test

<br/>

## case_node_port
- Node Exporter → OTel Collector → Prometheus / InfluxDB
- Node Exporter가 수집하고 OTel Collector가 중간 Aggregator 역할을 수행하는 구조

```text
+------------------------+
|     Host (Server)      |
| 🔹 Node Exporter        |
| - Expose /metrics 9100 |
+-----------+------------+
            |
            | scrape
            v
+----------------------------+
| OTel Collector (Aggregator)|
| - Scrape Node Exporter     |
| - Expose /metrics (9464)*  |
| - RemoteWrite to Influx    |
+---------------+------------+
                | scrape
        +-------+------------------------+
        |                                |
        v                                v
+-------------------+          +------------------------+
| Prometheus (9090) |          | InfluxDB (8086)        |
| - Scrapes 9464    |          | - Receives RemoteWrite |
| - Stores TSDB     |          |   from Prometheus      |
+-------------------+          +------------------------+

```

<br/>
<br/>

## case_otel_aggregator
- OTEL Agent가 먼저 메트릭을 받아 Collector(Aggregator)로 전달하는 이중 레이어 구조

```text
+------------------------+
|     Host (Server)      |
| 🔹 OTel Agent           |
| - OTLP gRPC (4317)     |
| - OTLP HTTP (4318)     |
+-----------+------------+
            |
            | OTLP Export
            v
+----------------------------+
|  OTel Collector (Aggregator)|
|  - Collect from Agent      |
|  - Expose /metrics (9464)  |
+---------------+------------+
                | scrape
        +-------+------------------------+
        |                                |
        v                                v
+-------------------+          +------------------------+
| Prometheus (9090) |          | InfluxDB (8086)        |
| - Scrapes 9464    |          | - Receives RemoteWrite |
| - Stores TSDB     |          |   from Prometheus      |
+-------------------+          +------------------------+

```

<br/>
<br/>
