# Data Cleaning and Preprocessing

# Handling Issues and Noise in the Data:
I aggregated demographic, migration, and real estate data from the Census API using two separate scripts, then combined this data with additional information from the Zillow API. The datasets for Colorado and Utah were concatenated based on zipcode, after which any rows containing negative values in categories where negatives are not feasible were dropped. These typically represented sparsely populated zip codes and thus did not significantly impact the overall analysis. I chose to remove these rows rather than impute missing values, as imputing would introduce artificial data, potentially skewing the analysis. Since the main focus was comparing densely populated zip codes in Colorado and Utah, dropping low-density zip codes with negative or missing values was a logical approach. These negative values likely occurred because the Zillow API lacked sufficient data for those specific areas.

# Understanding the Data:
Most of the features in the dataset are numerical, except for categorical variables like State, County, City, and Zip Code. Some features represent medians calculated from a limited sample size due to Zillow API restrictions, which allow for a maximum of 41 listings per zipcode. This limitation means the Zillow-derived columns should be interpreted cautiously, as they may not reflect the full distribution of real estate listings in areas where listings substantially exceed the 41-sample limit. Essentially, these medians are best viewed as a snapshot or random sample of Zillow's "front page" listings for each zipcode.

At this stage, we did not see the need to apply normalization to the dataset. However, for visualizations, we occasionally use logarithmic scaling to clearly display data distributions, especially when there are significant differences in scale across the dataset.

