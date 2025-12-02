# nvidia-smi

<br/>

## case_default
- **Telegraf → InfluxDB** 구조
- `nvidia-smi` 명령 기반 GPU 메트릭을 Telegraf Plugin으로 수집하여 InfluxDB에 저장하는 방식
- Prometheus 미사용 (InﬂuxDB 시계열에 직접 Write)

```text
+-----------------------------+
| GPU Host (Server)           |
| 🔹 NVIDIA GPU + Driver      |
| 🔹 Telegraf Agent           |
| - Executes nvidia-smi       |
| - Parse GPU metrics         |
| - HTTP write to InfluxDB    |
+-----------+-----------------+
            |
            | HTTP write
            v
+------------------------+
| InfluxDB (8086)        |
| - Receive from Telegraf|
| - Store Time-Series    |
+-----------+------------+
            |
            v
+------------------------+
|  Chronograf (8888)     |
| - Visualization UI     |
+------------------------+

```
