```mermaid
graph LR
    %% 1. 전체 메인 흐름 (가장 중요한 뼈대): 굵은 화살표(==>) 사용
    A["네트워크 트래픽 데이터 입력"] ==> B["1단계: 사전 학습<br>(Pretraining)"]
    C["2단계: 미세 조정<br>(Fine-tuning)"]
    B ==> D["최종 탐지"]
    
    %% 2. Phase 1 내부 상세 (일반 화살표 --> 사용)
    subgraph Phase1 ["Phase 1: 데이터 패턴 이해"]
        direction TB
        B1["데이터 증강<br>(노이즈 추가)"]
        B2["인코더(Encoder)<br>특징 압축"]
        B3["대조 학습<br>(SimCLR/NT-Xent)"]
        B1 --> B2 --> B3
    end

    %% 3. Phase 2 내부 상세 (일반 화살표 --> 사용)
    subgraph Phase2 ["Phase 2: 공격 탐지 훈련"]
        direction TB
        C1["학습된 인코더"]
        C2["분류기(Classifier)<br>결합"]
        C3["정상 vs 공격<br>학습"]
        C1 --> C2 --> C3
    end

    %% 4. 결과 출력 상세
    D1["정상 (Normal)"]
    D2["공격 (Anomaly)"]
    D --> D1
    D --> D2

    %% 5. 메인 단계와 세부 내용 연결 (설명적 연결): 점선(-.->) 사용
    %% 메인 노드(B)가 내부의 시작점(B1)을 포함한다는 느낌
    A -.-> B1
    %% Phase 1의 끝(B3)이 Phase 2의 시작(C)으로 이어진다는 흐름 보조 (선택 사항)
    B3 -.-> C
    %% 메인 노드(C)가 내부의 시작점(C1)을 포함한다는 느낌
    C -.-> C1
    

    
