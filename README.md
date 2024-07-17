# Sydney Area Bustling Score Analysis

## Project Overview

This repository contains the project report and code for calculating the bustling score of various SA2 regions in Sydney. The bustling score is determined based on multiple datasets including businesses, population, public transport stops, polling places, schools, traffic lights, public amenities, and pedestrian crossings.

## Data Description

### Datasets Used
- **Business.csv**: Data on different types of businesses in each SA2 region in NSW. Pre-processed by renaming the 'sa2_code' column to 'SA2_CODE21'.
- **Income.csv**: Data on income per SA2 region in NSW. Pre-processed by renaming 'sa2_code' to 'SA2_CODE21' and replacing 'np' values with NULL.
- **Population.csv**: Data on population numbers for each SA2 region in NSW. Pre-processed by renaming 'sa2_code' to 'SA2_CODE21'.
- **Stops.txt**: Data on public transport stops and their locations in Sydney. Pre-processed by converting latitude and longitude into POINT geometries and ensuring SRID matches (4326).
- **PollingPlace2019.csv**: Data on polling places and their locations in Sydney. Pre-processed by removing unwanted columns and converting latitude and longitude into POINT geometries.
- **Schools.shp**: Aggregated data on primary, secondary, and future catchment areas for schools in NSW.
- **SA2 digital boundaries**: Data on geometries of each SA2 region in NSW.
- **Traffic-lights-location-data-may-2021.csv**: Data on locations of all traffic lights in NSW. Pre-processed by converting latitude and longitude into POINT geometries.
- **Publicamenities.geojson**: Data on locations of public water fountains and toilets in NSW.
- **Crossings.geojson**: Data on locations of pedestrian crossings in NSW.

## Methodology

### Bustling Score Calculation
The bustling score for each SA2 region is calculated using the following steps:
1. **Z-Score Calculation**: For each dataset, z-scores are calculated to standardize the metrics.
   - **Z-business**: Number of retail trade, arts and recreation services, and accommodation and food services businesses per 1000 people.
   - **Z-stops**: Number of public transport stops per square kilometer.
   - **Z-polls**: Number of polling places per square kilometer.
   - **Z-schools**: Number of school catchment areas per 1000 young people (0-19 years).
   - **Z-traffic lights**: Number of traffic lights per square kilometer.
   - **Z-public amenities**: Number of public water fountains and toilets per square kilometer.
   - **Z-crossings**: Number of pedestrian crossings per square kilometer.

2. **Sigmoid Function**: The average of the z-scores is then passed through a sigmoid function to map the score between 0 and 1, providing the final bustling score.

### Correlation Analysis
Analyzed the relationship between bustling scores and median income, finding a weak positive correlation with a coefficient of 0.158.

## Findings
- The bustling scores mostly fall between 0.3 and 1, with a peak around 0.5.
- Regions closer to Sydney CBD are more bustling compared to the outskirts.
- Weak positive correlation between bustling scores and median income indicates other factors also contribute to an area's activity level.

## Visualizations
- A map highlighting the bustling scores of each SA2 region, with redder areas indicating higher scores.

## Future Work
- Extend the model to include more datasets for improved accuracy.
- Apply the bustling score methodology to other cities for comparative analysis.

## Authors
- Syed Ahmad Sabaat
- Frederic Max Serisier
- Duc Viet Hoang Vu

## References
- [FAOSTAT](https://www.fao.org/faostat/en/)
- [VisualCrossing](https://www.visualcrossing.com/)
- [Data NSW](https://data.nsw.gov.au/)
