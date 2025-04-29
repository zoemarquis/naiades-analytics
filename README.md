# Naïades project
[![License: MIT](https://img.shields.io/badge/License-MIT-lightgrey.svg)](https://opensource.org/licenses/MIT)
## 🔎 Overview
This project explores the relationship between the physicochemical properties of water and its biological state, using data from the [naiades](https://naiades.eaufrance.fr/) website.

The main objective is to understand these interactions and identify relevant spatial patterns such as hydroecoregions, while analyzing how different parameters influence aquatic ecosystems, specifically through the Multimetric Invertebrate Index (I2M2).

The analysis incorporates both temporal and spatial dimensions:

- **Temporal analysis**: Investigating how physicochemical parameters evolve over time and their delayed impact on biological indicators
- **Spatial analysis**: Examining whether natural groupings of stations based on their characteristics reflect hydroecoregions

## 🗂️ Data sources
The project uses several datasets:
- **Physicochemical data** (2005-2022): Contains measurements of 16 most commonly measured physicochemical parameters
- **Hydrobiological data** (2007-2022): Contains I2M2 calculation results
- **Station data**: Provides location information (latitude, longitude) and unique identifiers
- **Hydroecoregion data**: Spatial units defined based on similar ecological criteria

> ⚠️ Due to their large size, the datasets were not uploaded to this repository.

## ⚙️ Methodology

### 1. Data preparation
- **Cleaning the data**:
   - Removal of duplicates and outliers
   - Selection of relevant columns
   - Standardization of station identifiers

- **Data aggregation**:
   - Aggregation by station, season, and year
   - Calculation of summary statistics (median, mean)
   - Creation of datasets with different time lags (1 month, 3 months, 6 months)

- **Data integration**:
   - Joining physicochemical, hydrobiological, and station tables
   - Mapping stations to their respective hydroecoregions

### 2. Clustering analysis
- Implementation of K-means clustering to group stations based on their characteristics
- Determination of optimal number of clusters using elbow method, Davies-Bouldin coefficient, and silhouette score
- Comparison of clusters with actual hydroecoregions to evaluate coherence
- Analysis of different time lags to assess their impact on clustering results

### 3. Regression analysis
- Prediction of I2M2 from physicochemical parameters, spatial information, and temporal dimensions
- Use of 6-month lag for physicochemical parameters based on clustering results
- Implementation of regularization techniques (Lasso) to identify the most influential parameters
- Evaluation of model performance and interpretation of results

## ✨ Key findings
- About one-third of stations were correctly classified into their respective hydroecoregions through clustering

- The 6-month lag approach performed slightly better than the 1-month lag, suggesting that the impact of physicochemical data on hydrobiological state is more pronounced over longer periods

- The most discriminating parameters for hydroecoregion clustering were:
   - I2M2
   - Nitrates
   - Conductivity at 25°C
   - Organic carbon
   - Water temperature

- For I2M2 prediction, the most important parameters were:
   - Conductivity at 25°C
   - Nitrites
   - Organic carbon

- Negative correlations were observed between I2M2 and both conductivity at 25°C and nitrate concentrations


## 🚫 Limitations
- Seasonal bias in hydrobiological data (overrepresentation in summer)
- Loss of approximately 50% of stations during data joining
- Imbalance in the number of stations per region
- Extensive imputation of missing values using the median
- Limited exploration of different time lags

## 🌱Possible improvements
- Explore different value aggregation methods (e.g., mean instead of median)
- Test alternative temporal aggregations (monthly, yearly)
- Investigate additional time lags (e.g., 1 year) to better capture seasonal variations
- Implement alternative clustering approaches such as K-Means with Dynamic Time Warping or K-Medoids
- Balance the dataset to ensure equal representation of hydroecoregions

## 📝 Documentation
All analysis details, code, and results are available in the [notebook](naiades.ipynb) (in french), along with [HTML](naiades.html) and [PDF](naiades.pdf) exports of the notebook for easier viewing.

## 🎓 Academic context
This project was developed during the second year of the Master’s program in Data Science and Complex Systems at the University of Strasbourg.

The [original project assignment](./resources/project-assignment-fr.pdf) (in french) is also available for reference.

## 👷‍♂️ Contributors
- Zoé MARQUIS
- Charlotte KRUZIC
