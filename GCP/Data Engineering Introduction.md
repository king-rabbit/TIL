# Data Engineering :Introduction

- 데이터 엔지니어의 역할: 대시보드 또는 보고서, 머신러닝 모델을 위한 데이터 파이프라인 구축

    

- 데이터 레이크: 다양한 데이터(csv 파일, RDBMS, etc.)를 복제해서 한 곳으로 모은 것. 예를 들어 Cloud Storage bucket에 이러한 다양한 데이터를 모아서 데이터 레이크를 만들 수 있음.
- 데이터 웨어하우스: 데이터 레이크에 있는 데이터들을 ETL 파이프라인을 거쳐 분석용으로 저장한 것. (데이터가 보내지는 ending point = ‘data sync’이며, 보통 데이터 데이크의 데이터 싱크는 데이터 웨어하우스가 된다)

    

- GCP의 데이터 레이크용 서비스: Cloud Storage, Cloud SQL/Cloud Spanner(relational data), Firestore/Cloud Bigtable(NoSQL data)
- GCP의 데이터 웨어하우스 서비스: 빅쿼리. (빅쿼리 내 Datasets가 데이터 마트의 역할을 하게 됨)

    

- raw data를 가공해야 하는 경우
    - 배치 데이터 파이프라인의 경우 - Dataproc, Dataflow를 이용해 데이터 가공
    - 스트리밍 데이터 파이프라인의 경우 - Pub/Sub, Dataflow, BigQuery를 이용

- Data Governance / access 문제
    - Data Catalog: 데이터셋에 대한 메타데이터 제공. 데이터셋을 태그, flag로 그룹화할 수 있음.
    - Data Loss Prevention API: Data Catalog와 함께 사용. 신용카드 번호, 이름, 주민번호 등 보안이 중요한 데이터를 분류.
    
- Cloud Composer
    - 데이터 파이프라인를 관리하는 workflow orchestration 툴.
    - 아파치 Airflow의 fully-managed 버전.
    - 예를 들어 새로운 데이터가 들어왔을 때 데이터 파이프라인이 작동하도록 관리하는 툴로 볼 수 있음.