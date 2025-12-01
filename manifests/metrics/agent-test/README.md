# agent-test

<br/>

## case_hostmetrics
- **OpenTelemetry Collector → Prometheus / InfluxDB** 구조  
- 호스트 메트릭을 OTEL Collector가 직접 수집하는 방식

```text
+------------------------+
|     Host (Server)      |
| 🔹 HostMetrics Receiver |
+-----------+------------+
            |
            v
+----------------------------+
|  OTel Collector (Agent)    |
|  - Collect Host Metrics    |
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

## case_telegraf
- **Telegraf → Prometheus / InfluxD**B 구조
- Telegraf가 host metrics 수집 + Prometheus exporter 역할을 수행함

```text
+------------------------+
|     Host (Server)      |
| 🔹 Telegraf Agent       |
| - Host metrics input   |
| - Prometheus /metrics  |
| - HTTP write InfluxDB  |
+-----------+------------+
            |
            | scrape
        +---+------------------------------+
        |                                  |
        v                                  v
+-------------------+          +------------------------+
| Prometheus (9090) |          | InfluxDB (8086)        |
| - Scrapes metrics |          | - Receives from        |
| - Stores TSDB     |          |   Telegraf (HTTP)      |
+-------------------+          +------------------------+
```


<br/>
<br/>
