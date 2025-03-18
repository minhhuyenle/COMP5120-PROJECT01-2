# EMISSION DATASET

## Dataset Description
The Carbon Majors dataset is a historical database detailing production and emissions data from 122 of the world’s largest oil, gas, coal, and cement producers. It is designed to quantify both direct operational emissions and the emissions resulting from the combustion of marketed products attributable to these entities. The medium granularity version of the dataset contains the following key variables:

- **year (double):** The year for the recorded data point.
- **parent_entity (character):** The company or entity to which the emissions are attributed.
- **parent_type (character):** The classification of the entity; can be "investor-owned company", "state-owned entity", or "nation state".
- **commodity (character):** The type of commodity produced. This includes various forms of oil and natural gas liquids, different types of coal (e.g., Anthracite, Bituminous, Lignite, Metallurgical, Sub-Bituminous, Thermal), and Cement.
- **production_value (double):** The quantity of production, with units specific to each commodity:
  - **Oil & NGL:** Million barrels per year
  - **Natural Gas:** Billion cubic feet per year
  - **Coal & Cement:** Million tonnes per year
- **production_unit (character):** The corresponding unit for the production value.
- **total_emissions_MtCO2e (double):** The total emissions (in million tonnes of CO₂e) associated with the parent entity for that year.

This dataset spans back to 1854 and aggregates over 1.42 trillion tonnes of CO₂e, covering approximately 72% of global fossil fuel and cement emissions since the onset of the Industrial Revolution.

## Rationale for Selecting the Dataset
In light of the pressing environmental challenges and the significant impact of industrial activities on climate change, it is critical to examine the factors that drive emissions. My personal interest in environmental issues has led me to focus on exploring the determinants of emission levels, such as the types of products, industries involved, and their specific characteristics. The objectives of this study are to:

- Develop a comprehensive understanding of the emission characteristics across different commodity groups and industrial sectors.
- Propose actionable solutions for transitioning to green energy within industries, which may include incentives for investment, as well as strategies such as consumption restrictions, technical barriers, or the implementation of environmental taxes.

The selection of this dataset is driven by its comprehensive historical coverage, which provides the necessary depth for analyzing emission trends over time and comparing characteristics across various commodities—thereby laying a strong foundation for formulating targeted environmental policies.

## Research Questions & Analysis Plans

### 1. How have global emissions evolved over time?

**Question:**  
How have the total emissions from major entities changed over the years, and what are the key trends across different commodities?

**Plan:**

- **Variables involved:**  
  - `year`, `total_emissions_MtCO2e`, `commodity`

- **Steps:**
  1. **Visualization Techniques:**
     - Focus primarily on time series visualizations (line or area charts) to display the trends in total emissions over time.
     - Utilize interactive filters and slicers to allow users to isolate and examine the specific characteristics of each commodity group.
     - Incorporate scatter plots or similar visual formats to explore relationships between the year, emission levels, and commodity types.
     - Employ interactive Python libraries (such as Altair, Bokeh, or Plotly) to create dynamic and user-friendly visual interfaces.
  2. **Data Aggregation:**
     - Aggregate data by year and commodity to obtain a clear overview of emission trends.

### 2. What are the distinct emission and production patterns among entities?

**Question:**  
Can natural clusters be identified among entities based on their production and emissions data, and what characteristics define these clusters?

**Plan:**

- **Variables involved:**  
  - `parent_entity`, `parent_type`, `commodity`, `production_value`, `total_emissions_MtCO2e`

- **Steps:**
  1. **Data Preparation:**
     - Normalize production and emissions values to standardize scales across different commodities and entity types.
     - Generate additional features such as emissions intensity to enhance the analysis.
  2. **Clustering Analysis:**
     - Apply clustering algorithms (e.g., K-Means or Hierarchical clustering) to segment entities based on their production and emission profiles.
     - Use methods like the Elbow Method or Silhouette Score to determine the optimal number of clusters.
  3. **Dimensionality Reduction & Visualization (Optional):**
     - Utilize dimensionality reduction techniques (such as PCA) to project the data into a more interpretable visual space.
     - Create scatter plots or similar charts to visually represent the clusters and their relationships.
     - Leverage interactive visualization tools (e.g., Altair, Bokeh, or Plotly) to build an intuitive and engaging analysis interface.

## Additional Considerations

- **Data Cleaning & Preprocessing:**
  - Address missing or anomalous data points and standardize measurement units across different production types.
- **Visualization Tools:**
  - Prioritize interactive Python libraries such as Altair, Bokeh, or Plotly to develop dynamic visualizations that remain accessible without being overly complex.
