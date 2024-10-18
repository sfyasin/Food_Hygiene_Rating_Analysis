# Food Hygiene Rating Analysis using Food Standards Agency's API


## Table of Contents

- [Project Overview](#project-overview)
- [Key Aspect of the Project](#key-aspect-of-the-project)
- [Methodology](#methodology)
- [Tools](#tools)
- [Data Sources](#data-sources)
- [Code Example](#code-example)
- [Insights](#insights)
- [Recommendations](#recommendations)
- [Limitation](#limitation)


### Project Overview

This data analysis project aims to provide insights into the food hygiene rating in Sutton, South London over the past years. By analysing various aspects of the food hygiene data, we seek to gain deeper understanding of the trends and make data-driven recommendations to businesses and Food Standards Agency.


### Key Aspect of the Project

1. Hygiene Rating Distribution: Analysing the overall distribution of hygiene ratings across businesses in Sutton to identify patterns and anomalies.
2. Business Type and Hygiene Ratings: Investigating correlations between specific business types and their likelihood of receiving lower hygiene ratings.
3. Consistency of Low Ratings: Assessing whether certain business types consistently receive low ratings or if these ratings occur sporadically.
4. Geographical Trends in Ratings: Identifying geographic patterns in the distribution of high and low hygiene ratings across Sutton.


### Methodology

- Data Extraction: Accessing food hygiene data for Sutton via the Food Standards Agency’s API.
- Data Preparation: Conducting rigorous data cleaning, merging, and consistency checks to ensure data integrity.
- Exploratory Analysis: Employing Jupyter notebooks for an organised, data exploration and analysis workflow.
- Hypothesis Testing: Conducting statistical tests to evaluate differences in hygiene ratings across business types.
- Data Visualisation: Creating visualisations to effectively communicate key insights, including rating distributions and geographic patterns.


### Tools

The following Python libraries were used in this project:
- Pandas: for data analysis and manipulation
- Seaborn & Matplotlib: for visualisation
- Numpy & SciPy: for mathematical computations


### Data Sources

Food Hygiene Ratings Scheme (FHRS) Data
The data provides the food hygiene rating or inspection result given to a business and reflect the standards of food hygiene found on the date of inspection or visit by the local authority. Businesses include restaurants, pubs, cafés, takeaways, hotels and other places consumers eat, as well as supermarkets and other food shops.

The scheme gives businesses a rating from 5 to 0 which is displayed at their premises and online so you can make more informed choices about where to buy and eat food.
- 5 – hygiene standards are very good
- 4 – hygiene standards are good
- 3 – hygiene standards are generally satisfactory
- 2 – some improvement is necessary
- 1 – major improvement is necessary
- 0 – urgent improvement is required

[About this dataset](https://data.food.gov.uk/catalog/datasets/38dd8d6a-5ab1-4f50-b753-ab33288e3200)


### Code Example

Normalising data as it is nested.

```python
# Check if the request was successful (status code 200)
if response.status_code == 200:
    # Access the content of the response (the actual data)
    data = response.json()

    # Data is nested, flatten it using json_normalize
    # Import json_normalize
    from pandas import json_normalize  
    df = json_normalize(data)

    # Print the entire DataFrame to see all rows and columns
    with pd.option_context('display.max_rows', None, 'display.max_columns', None):
        print(df)
else:
    print("API request failed with status code:", response.status_code)
```


### Insights

The analysis results are summarised as follows:
1. Inspection Coverage: 84.3% of businesses have been inspected, 9.5% are 'Exempt' (low-risk establishments), and 6.2% are 'Awaiting Inspection,' indicating broad compliance with inspection requirements.
2. High-Rated Sectors: Healthcare, hospitality, and food distribution sectors generally receive higher ratings, likely due to stricter hygiene standards.
3. Low-Rated Takeaways: Takeaway and sandwich shops often score lower, with some rated as low as 1, suggesting challenges in maintaining hygiene in smaller, high-turnover businesses.
4. Geographical Patterns: No significant geographic differences in hygiene ratings were observed, indicating that factors like business type are more influential than location.


### Recommendations

Based on the analysis, we recommend the following actions:
1. Focus on Takeaway Businesses: Local authorities and the Food Standards Agency (FSA) should prioritise follow-up inspections and provide targeted guidance for takeaway and sandwich shops that consistently receive lower hygiene ratings.
2. Support Low-Rated Businesses: Introduce hygiene improvement programs to help struggling businesses improve their practices, especially those with ratings of 2 or lower.
3. Increase Public Awareness: Encourage consumers to actively check hygiene ratings before choosing where to eat, especially in areas where lower ratings are prevalent.


### Limitation
1. Data Freshness: The data reflects inspections up to a certain point, and newer inspections might not be reflected, limiting the real-time accuracy of the findings.
2. Geographic Scope: The analysis focuses on Sutton, South London, and the findings might not generalise to other regions without similar assessments.
3. Business Type Classification: Some businesses might have been categorised differently or inconsistently, leading to potential misinterpretation of trends within certain business types.

### References

1. [Food Standard Agency website](https://www.food.gov.uk/)
2. [Food Hygiene Rating Scheme](https://www.food.gov.uk/safety-hygiene/food-hygiene-rating-scheme)
