# Data Cleaning and Preprocessing

## Handling Issues and Noise in the Data:
I aggregated demographic, migration, and real estate data from the Census API using two separate scripts, then combined this data with additional information from the Zillow API. The datasets for Colorado and Utah were concatenated based on zipcode, after which any rows containing negative values in categories where negatives are not feasible were dropped. These typically represented sparsely populated zip codes and thus did not significantly impact the overall analysis. I chose to remove these rows rather than impute missing values, as imputing would introduce artificial data, potentially skewing the analysis. Since the main focus was comparing densely populated zip codes in Colorado and Utah, dropping low-density zip codes with negative or missing values was a logical approach. These negative values likely occurred because the Zillow API lacked sufficient data for those specific areas.

## Understanding the Data:
Most of the features in the dataset are numerical, except for categorical variables like State, County, City, and Zip Code. Some features represent medians calculated from a limited sample size due to Zillow API restrictions, which allow for a maximum of 41 listings per zipcode. This limitation means the Zillow-derived columns should be interpreted cautiously, as they may not reflect the full distribution of real estate listings in areas where listings substantially exceed the 41-sample limit. Essentially, these medians are best viewed as a snapshot or random sample of Zillow's "front page" listings for each zipcode.

At this stage, we did not see the need to apply normalization to the dataset. However, for visualizations, we occasionally use logarithmic scaling to clearly display data distributions, especially when there are significant differences in scale across the dataset.


## Basic Statistical Analysis 
The dataset comprises demographic, migration, and real estate variables for zip codes across Colorado and Utah. Summary statistics such as means, medians, variances, and standard deviations were computed to understand the central tendencies and spread of the data. For example, median home values average about \$332,143, while median household incomes average \$73,632, with substantial variation observed across zip codes. Variables like housing units, median gross rent, and population demographics also show wide variability, indicating diverse socioeconomic conditions across different areas. Several variables show signs of skewness, suggesting the presence of outliers or large differences between urban and rural zip codes.

## Correlations Between Features 
Exploring correlations revealed meaningful relationships between variables. Median household income positively correlates with median home values and median gross rents, indicating wealthier zip codes tend to have higher housing costs. Similarly, population density and migration patterns correlate with housing availability, suggesting areas with higher migration inflows tend to have increased demand and higher real estate prices.

## Data Similarity and Integration Analysis 
The dataset integrates data from two separate APIs: the Census Bureau (demographic and migration data) and Zillow (real estate data). Data was combined accurately at the zipcode level, ensuring consistency across states (Colorado and Utah). The integration was straightforward since the zip code acted as a reliable and standardized primary key across both datasets.

## Data Quality Assessment  
Data quality was assessed by checking completeness, consistency, and usability. Initially, there were issues like negative values in critical columns (median gross rent, home values, and incomes). Rows with these unrealistic values were removed, resulting in a cleaned dataset with 601 rows suitable for meaningful analysis. Missing values in Zillow-related features were noted due to API limitations, but these are expected and accounted for in the analysis.

## Alignment with Research Objectives  
The cleaned and integrated dataset aligns directly with the project's research objectives, facilitating a detailed comparison of the cost of living, demographic characteristics, and migration patterns between major cities like Denver and Salt Lake City. The completeness and reliability of the data are sufficient to address questions about housing affordability, demographic composition, and the factors driving migration in and out of these states.
