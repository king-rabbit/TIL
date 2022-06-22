# GCP: 데이터파이프라인 관련 제품

## Ingestion & Process

### Pub/Sub

- 여러개의 데이터 소스로부터 메시지를 받아 Dataflow로 메시지를 보냄.
- 데이터 종류에 따라 여러개의 Topic이 있을 수 있음(ex. Human Resources Topic - employee data)
- Topic을 구독하는 Subscriber들이 메시지를 전송받게 됨.
- 여러개의 Topic이 있을 수 있고, Subscriber도 여러개 있을 수 있음.

### Dataflow

- Pub/Sub의 메시지를 받은 후 데이터 웨어하우스로 데이터를 전송하는 역할.
- 실시간 데이터/ 배치 데이터 모두 가능.
- Apache Beam pipeline을 실행하는 fully managed service.
- Graph optimization → Work scheduler → Auto-scaler → Auto-healing → Work rebalancing → Compute & Storage
- Streaming/Batch/Utility templates 중 하나를 고를 수 있음.

## Storage

### for Unstructured Data: Cloud Storage

- Standard Storage: Hot Data. 데이터가 자주 읽히고 쓰이는 디비.
- Nearline Storage: Once per month
- Coldline Storage: Once every 90 days
- Archive Storage: Once a year

### for Structured Data

- for Transactional workload
    - Cloud SQL: Local/regional scalablity, SQL
    - Cloud Spanner: Global scalability, SQL
    - Firestore: NoSQL
- for Analytical workload
    - BigQuery: SQL
    - Cloud Bigtable: NoSQL