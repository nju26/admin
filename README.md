```mermaid
graph LR
    %% 스타일 정의
    subgraph P1 [Phase 1: Visualization & Localization]
        direction TB
        Gen1("<b>[1세대] Pixel Level</b><br/>Input Gradient<br/>(Saliency Map)")
        Gen2("<b>[2세대] Region Level</b><br/>Feature Map<br/>(Grad-CAM)")
    end

    subgraph P2 [Phase 2: Semantic Understanding]
        direction TB
        Gen3("<b>[3세대] Attribution</b><br/>Contribution Score<br/>(LRP, IG)")
        Gen4("<b>[4세대] Concept</b><br/>Human Concept<br/>(TCAV)")
    end

    subgraph P3 [Phase 3: Reasoning & Generation]
        direction TB
        Gen5("<b>[5세대] Generative</b><br/>Counterfactual<br/>(Diffusion XAI)")
        Gen6("<b>[6세대] Foundation</b><br/>Multi-modal<br/>(CLIP, SAM)")
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
    C -.-> C1
    

    
