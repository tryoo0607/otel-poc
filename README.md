# otel-poc

<br/>

## 프로젝트 개요

**otel-poc** 는 OpenTelemetry 기반 메트릭 수집 및 관측성 구조 테스트를 위한 PoC 용도.

- OpenTelemetry Collector를 이용한 데이터 수집 경로 검증
- 다양한 Exporter 및 Observability 백엔드 연동 실험
- 벤더 종속 없는 통합 관측성 파이프라인 구성 확인
- Kubernetes 기반 배포 실험 및 Collector 구조 검증

<br/>
<br/>

## 구성 요소

| 경로 | 설명 |
|------|------|
| `configs/` | Collector Receivers / Processors / Exporters 설정 파일 |
| `manifests/` | Kubernetes 배포 및 테스트 환경 구성 매니페스트 |
| `README.md` | 사용 가이드 및 실험 결과 정리, `manifests/` 하위에서만 작성 |


<br/>
<br/>



## ENV
- ${OTEL_POC_DIR} : 이 프로젝트 Root 경로
- ${OTEL_POC_VOLUMES} : 데이터 저장 위한 경로
