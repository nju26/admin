```mermaid
graph LR
    A["네트워크 데이터 입력"] --> B["1단계: 사전 학습<br>(Pretraining)"]
    B --> C["2단계: 미세 조정<br>(Fine-tuning)"]
    C --> D["최종 탐지"]
    
    subgraph Phase1 ["Phase 1: 데이터 패턴 이해 (정답 X)"]
        direction TB
        B1["데이터 증강<br>(노이즈 추가)"]
        B2["인코더(Encoder)<br>특징 압축"]
        B3["대조 학습<br>(SimCLR/NT-Xent)"]
        B1 --> B2 --> B3
    end

    subgraph Phase2 ["Phase 2: 공격 탐지 훈련 (정답 O)"]
        direction TB
        C1["학습된 인코더"]
        C2["분류기(Classifier)<br>결합"]
        C3["정상 vs 공격<br>학습"]
        C1 --> C2 --> C3
    end

    D1["정상 (Normal)"]
    D2["공격 (Anomaly)"]
    D --> D1
    D --> D2

    %% 연결선 정리 (메인 노드와 세부 과정 연결)
    B -.-> B1
    B3 -.-> C
    C -.-> C1
