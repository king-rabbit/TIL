# Cloud Storage

- Cloud Storage는 buckets와 objects라는 두가지 요소로 구성됨.
    - buckets
        - objects를 갖고 있는 컨테이너이며, objects안에 데이터가 보관됨.
        - 글로벌하게 unique한 이름을 가지기 때문에 한번 이름을 정하면 바꿀 수 없음.
        - 버킷은 단일 region이나 여러개의 region에 속함. 데이터가 있는 곳과 가까운 region으로 정하는 것이 속도 측면에서 좋음.
    - objetcs
        - 오브젝트가 저장되면 cloud storage는 오브젝트를 복제하고 이들 오브젝트 중 유실되는 케이스가 생기면 다른 오브젝트에서 복제해 저장함.
        - multi region 버킷인 경우에는 오브젝트가 리전에 걸쳐 복제되며, 단일 리전 버킷의 경우 오브젝트가 zone에 걸쳐 복제됨.
        - 오브젝트는 metadata와 함께 저장되며 메타 데이터는 액세스를 관리하거나 암호화 기능 등에 사용됨.
        
- Storage Classes
    - Standard Storage: 자주 액세스해야 하는 데이터(hot data)용. 또는 일시적으로만 저장할 데이터용.
        - 단일 리전에서 사용하면 computation 성능을 높일 수 있음.
        - 멀티 리전에서 사용하는 경우 전세계적으로 액세스가 필요한 데이터를 저장하는 데 적합함. 예를 들어 웹사이트 콘텐츠나 스트리밍 비디오 같은 경우.
    - Nearline Storage: 저비용에 내구성이 높은 데이터 저장 서비스. 가끔 액세스하는 데이터용으로 적합함. availability가 상대적으로 낮고 최소 30일간 저장하는 경우에 적합.
        - 한달에 평균 1번 또는 더 적게 데이터를 읽거나 수정하는 경우에 이상적임.
        - 데이터 백업용, 롱테일 미디어 콘텐츠, 데이터 아카이빙용으로 적합함.
    - Coldline storage: 저비용, highly durable 스토리지.
        - 최소 90일간 저장하는 경우에 적합함. 분기별로 한 번 정도 읽거나 수정하는 경우 적합함.
    - Archive Storage: 데이터 아카이빙, 온라인 백업, 복원용 스토리지 서비스.
        - 최소 365일 이상 데이터 저장용으로 적합. 1년에 1번 정도 데이터를 조회하는 경우에 적합함.
    
- Cloud Storage simulates a file system
    - 클라우드 스토리지에서는 파일 시스템과 유사한 시스템을 사용함
    - buckt명/objetct명/ 식으로 파일 구조와 유사한 구조임.
    
- Object management features
    - retention policy: 오브젝트를 몇일간 보관할지 지정
    - versioning: 버전 관리
    - lifecycle management: 몇일간 액세스가 없는 경우 nearline, coldline으로 스토리지 클래스 변경
    
- 액세스 Control
    - IAM
        - bucket roles 설정: Reader / Writer / Owner / Set ACL policy
    - access lists(ACL)
        - IAM과 별개로 특정 object에 대한 access 권한을 줄 수 있음.
        
- Data encryption options
    - 구글 클라우드의 모든 데이터는 GMEK (Google-managed encryption keys)를 통해 암호화됨.
    - CMEK(customer-managed encryption keys), CSEK(customer-supplied encryption keys)을 이용할 수도 있음.
    - Client-side encryption: 데이터를 업로드하기 전에 암호화함.