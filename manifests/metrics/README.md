# metrics
CPU, MEMORY 등의 GPU 제외한 메트릭 정보를 수집하기 위한 설정 모음

<br/>
<br/>


## 하위 프로젝트
- `agent-test/`
  - `수집기 -- 백엔드(influxdb, prometheus 등)`
  - 수집기와 백엔드를 직접 연결하는 패턴으로 구성한 테스트 항목들


- `aggregator-test/`
  - `수집기 -- otel -- 백엔드`
  - 위와 같이 수집기와 백엔드 사이에 OTEL을 Aggregator로 사용하는 패턴으로 구성한 테스트 항목들


<br/>
<br/>
