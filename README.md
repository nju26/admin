```mermaid
graph LR

    %% Phase 1: 시각화 및 위치 파악
    subgraph P1 [Phase 1: Visualization & Localization]
        direction TB
        Gen1("<b>[1세대] Pixel Level</b> (2013~)<br/>Q: 어디가 중요한가?<br/>(Saliency Map, DeconvNet)<br/>- Gradient 시각화, 노이즈 多")
        Gen2("<b>[2세대] Region Level</b> (2016~)<br/>Q: 어느 영역을 보았는가?<br/>(CAM, Grad-CAM)<br/>- 직관적 Heatmap")
    end

    %% Phase 2: 의미적 이해
    subgraph P2 [Phase 2: Semantic Understanding]
        direction TB
        Gen3("<b>[3세대] Attribution</b> (2015~17)<br/>Q: 왜 그렇게 예측했는가?<br/>(LRP, IG, DeepLIFT)<br/>- 수학적 기여도 분해")
        Gen4("<b>[4세대] Concept</b> (2018~)<br/>Q: 어떤 개념이 작용했는가?<br/>(TCAV, ACE)<br/>- 인간이 이해하는 개념(Semantic)")
    end

    %% Phase 3: 추론 및 생성
    subgraph P3 [Phase 3: Reasoning & Generation]
        direction TB
        Gen5("<b>[5세대] Generative</b> (2019~23)<br/>Q: 바꾼다면 어떻게 되는가?<br/>(Counterfactual, Diffusion XAI)<br/>- 이미지 조작/생성 검증")
        Gen6("<b>[6세대] Foundation</b> (2023~)<br/>Q: 모델은 어떻게 추론하는가?<br/>(CLIP, SAM, GPT-4V)<br/>- 멀티모달, 자연어 설명")
    end

    %% 연결선
    Gen1 --> Gen2
    Gen2 ==> Gen3
    Gen3 --> Gen4
    Gen4 ==> Gen5
    Gen5 --> Gen6

    %% 클래스 적용
    class Gen1,Gen2 phase1;
    class Gen3,Gen4 phase2;
    class Gen5,Gen6 phase3;

    
