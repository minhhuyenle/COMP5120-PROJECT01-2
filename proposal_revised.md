# EMISSION DATASET

## Dataset Description

The **Carbon Majors dataset** is a historical database detailing production and emissions data from **122 of the world’s largest oil, gas, coal, and cement producers**, compiled since 1854 (with acknowledgment to *Data is Plural* for highlighting the resource). This dataset, often referred to as *Carbon Majors*, quantifies both the direct operational emissions and the emissions from the combustion of marketed products attributable to these entities. It encompasses:

- 75 Investor-owned Companies  
- 36 State-owned Companies  
- 11 Nation States  
- 82 Oil Producing Entities  
- 81 Gas Entities  
- 49 Coal Entities  
- 6 Cement Entities  

Collectively, the data spans back to **1854** and contains over **1.42 trillion tonnes of CO₂e**—covering approximately **72% of global fossil fuel and cement emissions** since the start of the Industrial Revolution (1751). Carbon Majors provides low-, medium-, and high-granularity datasets; for this project, the **medium** granularity dataset is used. It includes:

- **year (double):** The year for the recorded data point.  
- **parent_entity (character):** The company or entity to which the emissions are attributed.  
- **parent_type (character):** The classification of the entity: `"investor-owned company"`, `"state-owned entity"`, or `"nation state"`.  
- **commodity (character):** The type of commodity produced (e.g., oil, natural gas, coal variants, cement).  
- **production_value (double):** The annual volume of production (with units such as million barrels, billion cubic feet, or million tonnes, depending on the commodity).  
- **production_unit (character):** The corresponding unit for the production value.  
- **total_emissions_MtCO2e (double):** The total emissions (in million tonnes of CO₂e) associated with the parent entity for that year.  

By offering comprehensive historical coverage—tracing emissions sources across various industrial sectors—this dataset is well-suited for analyzing emission trends over time and comparing characteristics across commodities and entity types.

---

## Rationale for Selecting the Dataset

In light of the pressing environmental challenges and the significant impact of industrial activities on climate change, it is critical to examine the factors that drive emissions. My personal interest in environmental issues has led me to focus on exploring the determinants of emission levels, such as the types of products, industries involved, and their specific characteristics. The key objectives of this study are to:

- Develop a comprehensive understanding of the emission characteristics across different commodity groups and industrial sectors.  
- Propose actionable solutions for transitioning to green energy within industries, which may include incentives for investment, as well as strategies such as consumption restrictions, technical barriers, or the implementation of environmental taxes.  
- Assess the influence of policy milestones (e.g., Kyoto Protocol, Paris Agreement) to investigate whether or how these international accords correlate with notable shifts in emissions trends.

The selection of this dataset is also driven by the breadth of its historical scope, providing a strong foundation for analyzing long-term emission trends. By including commodity-specific production data, the dataset further enables investigation of **emission intensity**—emissions per unit of production—which is crucial for gauging industrial efficiency and evaluating policy interventions.

---

## Research Questions & Analysis Plans

### 1. How have global emissions evolved over time?

**Question**  
> How have the total emissions from major entities changed over the years, and what are the key trends across different commodities?  
> Additionally, how do policy milestones (e.g., the Paris Agreement or COP commitments) align with observed changes in emissions over time?

**Plan**

- **Variables involved**  
  - `year`, `total_emissions_MtCO2e`, `commodity`, `parent_type`, *(potentially)* external data on policy milestones or national commitments

- **Steps**  
  1. **Visualization Techniques**  
     - Use time series visualizations (line or stacked area charts) to display trends in total emissions over time.  
     - Include interactive filters to allow users to isolate specific commodities or ownership types.  
     - Incorporate scatter plots (or similar) to explore relationships between time, emission levels, and commodity types.  
     - Annotate major policy events (Kyoto Protocol, Paris Agreement, COP sessions) on the timeline to see if there are noticeable shifts around those dates.

  2. **Data Aggregation & Emission Intensity**  
     - Aggregate data by year and commodity for a clear overview of emission trends.  
     - Compute **emission intensity** (e.g., `emissions / production_value`) to assess efficiency changes over time.  
     - Compare emission intensity across different commodities or ownership types (investor-owned vs. state-owned vs. nation state).

  3. **Additional External Data (Optional)**  
     - If feasible, merge an external dataset capturing the years in which various nation-states or entities pledged emissions commitments (COP, NDC targets, etc.).  
     - Investigate whether these commitments correlate with any discernible changes in emission levels.

---

### 2. What are the distinct emission and production patterns among entities?

**Question**  
> Can natural clusters be identified among entities based on their production and emissions data, and what characteristics define these clusters?

**Plan**

- **Variables involved**  
  - `parent_entity`, `parent_type`, `commodity`, `production_value`, `total_emissions_MtCO2e`, plus derived metric `emission_intensity`

- **Steps**  
  1. **Data Preparation**  
     - Normalize production and emissions values to standardize scales across different commodities (e.g., **z-score normalization** or converting all production to a single energy unit).  
     - Generate **emissions intensity** (CO₂e per unit of production) to improve clustering accuracy and interpretability.

  2. **Clustering Analysis**  
     - Apply **K-Means** or **Hierarchical Clustering** to group entities based on their production and emission profiles.  
     - Use the **Elbow Method** or **Silhouette Score** to determine the optimal number of clusters.  
     - Present the clustering results visually (e.g., silhouette plots, scatter plots, or heatmaps).

  3. **Dimensionality Reduction & Visualization (Optional)**  
     - Employ techniques like **PCA** to reduce dimensionality, then create 2D or 3D scatter plots for an intuitive view of clusters.  
     - Provide an interactive interface (e.g., Altair, Bokeh, Plotly) to allow users to filter by `parent_type`, `commodity`, or `emission_intensity` ranges.

  4. **Interpretation**  
     - Examine the characteristics of each cluster (commodity types, emission intensities, ownership type, etc.). 
---

## Additional Considerations

- **Data Cleaning & Preprocessing**  
  - Address missing or anomalous data points.  
  - Standardize measurement units (barrels, cubic feet, tonnes) for consistent comparisons across commodities.  
  - Validate external policy data for timeline alignment if merging information on COP, Paris, or other agreements.

- **Visualization Tools**  
  - Prioritize **Altair**, **Bokeh**, or **Plotly** for interactive, user-friendly visuals.  
  - Use **stacked area charts** to illustrate how different commodities contribute to total emissions over time, annotated with global policy milestones.  
  - Consider **parallel coordinate plots** or **heatmaps** for multidimensional clustering analysis.
