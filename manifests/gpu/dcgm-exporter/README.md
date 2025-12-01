# dcgm-exporter

<br/>

## case_default / case_custom
- **DCGM Exporter → OTel Collector → Prometheus** 구조
- GPU 메트릭을 DCGM Exporter가 수집하고 OTEL Collector가 scrape 대상 엔드포인트를 제공하는 방식
- case_custom 은 **커스텀 GPU metric counter 목록(default-counters.csv) 적용** 차이


```text
+----------------------------+
| GPU Host (Server)          |
| 🔹 NVIDIA GPU + Driver     |
| 🔹 DCGM Exporter (host mode)|
| - Expose /metrics (9400)   |
+--------------+-------------+
               |
               | scrape
               v
+----------------------------+
|  OTel Collector (Agent)    |
|  - Scrape DCGM Exporter    |
|  - Expose /metrics (9464)  |
+---------------+------------+
                | scrape
        +-------+------------------------+
        |                                |
        v                                v
+-------------------+          +------------------------+
| Prometheus (9090) |          | InfluxDB (Optional ✓ ) |
| - Scrapes 9464    |          | Not enabled by default |
| - Stores TSDB     |          | (Config extendable)    |
+-------------------+          +------------------------+

```

<br/>
<br/>
