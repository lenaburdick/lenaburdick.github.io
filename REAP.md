Here is a simple flow chart:

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

```mermaid
graph TD
    A["`**LNG Spot Prices**
    LNG Spot Price Assessment.xlsx`"];
    B["`**Parameter Estimates**
    Project Mean Reversion.xlsx`"];
    C[Reversion Model];
    D["`**Inputs Document**
    Project Spend - RPS.xlsx`"];
    E["`**Tariff Model**
    ACEP tariff Model - RPS.xlsx`"];
    F[Main]
    G[Output]
    H[Yearly Gas Costs]
    I[Yearly Fuel Costs]
    J[Yearly Total Energy Costs]
    K["`**Simulation Results**
    Simulation_Results.xlsx`"];


    A --> B;
    B --> F;

    D --> E;
    E --> H;

    F --> G;
    G --> H;
    H --> I;
    I --> J;
    J --> K;

    subgraph C["`**Reversion Model**
    Simulation-Reversion-Model_With-Macros.xlsm`"]
        F[Main];
        G[Output];
        H[Yearly Gas Costs];
        I[Yearly Fuel Costs];
        J[Yearly Total Energy Costs];
    end
    style F fill:#48c78f,stroke:#333,stroke-width:2px;
    style G fill:#48c78f,stroke:#333,stroke-width:2px;
    style H fill:#48c78f,stroke:#333,stroke-width:2px;
    style I fill:#48c78f,stroke:#333,stroke-width:2px;
    style J fill:#48c78f,stroke:#333,stroke-width:2px;

```
