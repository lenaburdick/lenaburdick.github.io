

```mermaid
flowchart TD
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


---

## Workbooks


LNG Spot Prices
------
<details>
<summary> Workbook Description </summary>
-Collects various sources for natural gas spot prices
-Runs regression to fill in gaps in data
-Produces LNG price data for each month of a 10-year period
</details><br/>




Parameter Estimates
------
<details>
<summary> Workbook Description </summary>
-Uses LNG regression data
-Estimates relevant parameters and volatilities for mean reversion model
</details><br/>



Inputs Document
------
<details>
<summary> Workbook Description </summary>
-Breaks new renewable energy infrastructure purchases into 23 separate projects (9 solar, 14 wind) which begin development, construction, and production in different years.
-Allows users to change model parameters, cost/schedule inputs, assumptions about technological advancements and region-specific factors.
-Indexes various schedule information to be easily used by Tariff Model.
</details><br/>



Tariff Model
------
<details>
<summary> Workbook Description </summary>
-Calculates various metrics for each project including but not limited to subsidies, CapEx, AFUDC, Book Depreciation, Tax Depreciation, ADIT, Traditional Cost of Service, and Levelized Cost of Service
-Uses yearly expenditures of each project to find yearly expenditures of all projects, which are then used to find the “Yearly Total Energy Costs” for the RPS plan.
</details><br/>



Reversion Model
------
This is the project's main model. It includes several sheets which build ontop of one another to produce final results.

<details>
<summary> Main </summary>
    
**Process:** Uses user inputs (e.g. from Parameter Estimates) to generate a sample price path with monthly data <br/>
**Result:** Generates new sample path each time sheet is refreshed

</details><br/>

<details>
<summary> Output </summary>
    
**Process:** Uses a VBA Macro to record 1000 sample price paths generated from “Main” sheet.
**Result:** Monthly LNG prices - 1000 rows

</details><br/>


<details>

<summary> Yearly Gas Costs </summary>
    
**Process:** <br/>
Averages the monthly data for each year of the simulation using a VBA macro. <br/>

**Result:** <br/>
Yearly LNG prices - 1000 rows

</details><br/>


<details>

<summary> Yearly Fuel Costs </summary>
    
**Process:** <br/>
Adds yearly predicted coal and oil prices (from NREL data) to yearly LNG prices. Does this for both RPS and BAU cases. Uses inflation assumptions to calculate both nominal costs and real costs. <br/>

**Result:**
- Yearly Fuel prices under RPS plan (nominal & real) - 1000 rows (each)
- Yearly Fuel Prices under BAU plan (nominal & real) - 1000 rows (each)

</details><br/>


<details>

<summary> Yearly Total Energy Costs </summary>
    
**Process:** <br/>
Adds yearly predicted fuel costs to yearly predicted non-fuel costs. Most predicted non-fuel costs are taken from NREL data. “Renewable Purchases” for the BAU case are taken from NREL data, but the RPS data were calculated by Tariff Model. Non-variable Generation Costs were calculated separately, as the NREL data only accounted for variable costs. Yearly energy usage data was used to calculate the yearly cost to consumers. <br/>

**Result:**
- Yearly Total Energy Cost (nominal) for RPS & BAU Plan - 1000 rows (each)
- Yearly Price Per KWh for RPS & BAU Plan - 1000 rows (each)
- Yearly Cost to Consumers for RPS & BAU Plan - 1000 rows (each)

</details><br/>




Simulation Results
------
<details>
<summary> Workbook Description </summary>
    
**Process:** <br/>
A VBA macro copies description information from Reversion Model and Inputs Document, as well as data from “Yearly Total Energy Costs.” It copies values only, so that once they are produced, these results can be analyzed without needing a connection to the other documents. <br/>

**Result:**
- “Runs Summary” sheet for both BAU & RPS case with a table of Yearly Fuel Costs, Energy Costs, Price Per kWH, and Cost to Consumers
- Multiple sheets of analysis and graphs
</details><br/>




## VBA Macros








