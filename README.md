# Effect of Sea Level Rise on train stations in Yokohama

Sea level rise refers to an increase in the total volume of ocean water. It is caused by the melting of glaciers and the expansion of seawater as it warms, both of which result from climate change.

This rise poses a serious threat to coastal cities, where large population centers are often located. As water levels increase, urban infrastructure such as public transportation stations becomes more vulnerable to flooding and service interruptions. In the worst case scenario, they may be completely submerged. This is especially important in cities like Yokohama, Japan, much of which is built on reclaimed land just above sea level. In addition, its public transportation system relies on a complex and highly interconnected network, and losing one of the stations could disrupt service across multiple lines.

This project focuses on identifying gaps in the resilience of Yokohama’s railway stations to sea level rise. By mapping stations at risk of flooding and analyzing future vulnerabilities under different sea level scenarios, we aim to pinpoint areas with lack of insufficient connectivity and low elevation. The goal is to support planning efforts that maintain accessibility and ensure reliable transport despite the challenges posed by climate change.


## Data

Data
This project employs data from three different sources.

One of which is the using the The Sea Level Explorer Data to determine the sea level rise. The Sea Level Explorer was developed by NASA in collaboration with the United States Department of Defense, United States Department of State, and The World Bank. The Explorer delivers the latest information on past, present and future sea level change for every coastal country on Earth.

Data Source: https://climateknowledgeportal.worldbank.org/download-data#htab-1503

Second, OpenStreepMap data was gathered using the osmnx library to obtain the geographic coordinates and names of railway stations.

Lastly, the elevation digital dataset was retriced through the tessaDEM API to obtain the values for elevation for the region of interest. TessaDEM API merged and adjusted multiple sources according to tree height, urbanization and water presence using AW3D30, MERIT DEM, Forest Height, World Settlement Footprint and Global Surface Water.


## Models Evaluated


- Ordinary Least Squares (OLS): Used as the primary baseline to calculate the historical average rate of rise.


- Facebook Prophet: A Bayesian additive model used to decompose the signal into its core components:
  - Trend: Captures the non-linear acceleration of sea levels.
  - Seasonality: Automatically identifies the annual steric cycle (thermal expansion and meltwater runoff).

 The final model achieved a train RMSE of 3.45mm and a test RMSE of 3.74mm. 
<img width="962" height="442" alt="image" src="https://github.com/user-attachments/assets/d85e3a94-fa4c-4b41-ad32-5407eeeecb04" />



Using this model to make predictions, we were able to identify 7 stations at risk of being submerged and 1 submerged by 2250.


## Limitations
- Conservative Bias: By relying on historical trends, this model likely provides a "conservative" estimate compared to physics-based projections.

- The data may not reflect the exact elevation of sub-surface platforms or specialized railway infrastructure, creating a margin of error in our "at-risk" assessments.
