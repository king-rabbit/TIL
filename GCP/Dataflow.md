# Dataflow

- Apache Beam 기반의 데이터 파이프라인 시스템

### Apache Beam

- 배치 시스템과 스트리밍 시스템을 결합시킨 것이 특징.
- PTransforms: Inputs - Transforms - Outputs로 이어지는 데이터 처리 abstraction(action or code)
- PCollections
    - 데이터 abstraction으로 immutable함. (Any change that happens in a pipeline ingests one P collection and creates a new one. It does not change the incoming P collection.)
    - 배치/스트리밍 데이터 모두 포함. 스트리밍 PCollection은 Unbounded PCollection으로 사이즈가 정해져 있지 않고, 배치 데이터는 Bounded PCollection으로 사이즈가 정해져 있음.
    - 모든 데이터는 serialized byte strings로 저장됨.