# World Happiness Report


## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools Used](#tools-used)
- [Data Loading and Cleaning](#data-loading-and-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Visualizations](#visualizations)
- [Result and Findings](#result-and-findings)
- [Recommendations](#recommendations)
- [Closing Remarks](#closing-remarks)



### Project Overview

The goal of this project is to conduct an exploratory data analysis (EDA) on the World Happiness dataset using Python. The dataset encompasses various factors such as GDP, social support, life expectancy, freedom, trust in government, and overall happiness scores across different regions and countries.

### Data Sources

World Happiness Dataset: This dataset was obtained from kaggle in a csv format, containing different columns and informations about human factors, happiness score, regions, country and more.

### Tools Used

- Excel: used for data cleaning
- Python: Its used for data cleaning, data exploratory, and visualization

### Data Loading and Cleaning

- Import the necessary Python libraries, including Pandas and Matplotlib.
- Load the World Happiness dataset into a Pandas DataFrame.
- Perform data cleaning to handle missing values, removing duplicates and any inconsistencies in the dataset.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

%matplotlib inline
```
```python
df = pd.read_csv(r'C:\\Users\\HP\\Desktop\\2015.csv')
```
```python
# Lets drop missing value with this line of code
df.dropna(axis=0, inplace = True)
```
```python
# Drop duplicates values
df = df.drop_duplicates(keep='first')
```
**Notes**: Our dataset was very cleaned, so its required less effort.

### Exploratory Data Analysis

- What is the relationship between happiness score and region?
- What effect does freedom have on happiness score across all region?
- How does Happiness Score affect Health (Life Expectancy) across different Region?
- Does Trust (Government Corruption) affect Happiness Score across Regions?

### Data Analysis

**Lets include some of interesting python code used for our analysis:**

```python
# Grouping Happiness score by regions
group_data = df.groupby('Region')['Happiness Score'].mean()
# Printing our results
group_data
```

```python
# Group data by region
grouped = df.groupby('Region')
# Calculate the average freedom score for each region and their happiness score
region_stats = grouped[['Freedom', 'Happiness Score']].mean()
# Sorting the region based on their freedom score in descenging order
sorted_regions = region_stats.sort_values('Freedom', ascending=False)
#Print result
print(sorted_regions)
```

```python
# Group data by region
grouped = df.groupby('Region')
# Calculate the average Health (Life Expectancy) score for each region and their happiness score
region_stats = grouped[['Health (Life Expectancy)', 'Happiness Score']].mean()
# Sorting the region based on their freedom score in descenging order
sorted_regions = region_stats.sort_values('Health (Life Expectancy)', ascending=False)
#Print result
print(sorted_regions)
```

```python
# Group data by region
grouped = df.groupby('Region')
# Calculate the average trust score for each region and their happiness score
region_stats = grouped[['Trust (Government Corruption)', 'Happiness Score']].mean()
# Sorting the region based on their freedom score in descenging order
sorted_regions = region_stats.sort_values('Trust (Government Corruption)', ascending=False)
#Print result
print(sorted_regions)
```

### Visualizations

**Lets includes our visualization and their derivatives python codes:**

```python
# Plotting a bar chart for our data
plt.figure(figsize=(12, 6))

group_data.plot(kind='bar', color = 'green')
plt.xlabel('Region')
plt.ylabel('Average Happiness Score')
plt.title('Average Happiness score according to their region')
plt.show()
```

![output_19_0](https://github.com/kunmy94/Data-Exploration-in-Python-Project/assets/139684981/a2a1adca-a5f1-4e1e-86b7-c14ad0f7b770)


```python
plt.figure(figsize=(12, 6))

sorted_regions.plot(kind='bar', color = ['green', 'blue'])
plt.xlabel('Region')
plt.ylabel('Average Happiness Score and Freedom')
plt.title('Average Happiness score and Freedom according to their region')
plt.show()
```

![output_23_1](https://github.com/kunmy94/Data-Exploration-in-Python-Project/assets/139684981/d141b9f9-70fd-485b-aa7f-eb02f3ac6722)



```python
plt.figure(figsize=(14, 8))

sorted_regions.plot(kind='bar', color = ['red', 'blue'])
plt.xlabel('Region')
plt.ylabel('Average Health (LIfe Expectancy) and Happiness Score')
plt.title('Average Happiness score and Health (LIfe Expectancy) according to their region')
plt.show()
```


![output_27_1](https://github.com/kunmy94/Data-Exploration-in-Python-Project/assets/139684981/4c512522-05b5-4900-900d-9e6ce0175465)


```python
plt.figure(figsize=(16, 10))

sorted_regions.plot(kind='bar', color = ['black', 'yellow'])
plt.xlabel('Region')
plt.ylabel('Average Trust (Government Corruption)  and Happiness Score')
plt.title('Average Happiness score and Trust (Government Corruption) according to their region')
plt.show()
```


![output_31_1](https://github.com/kunmy94/Data-Exploration-in-Python-Project/assets/139684981/569b4856-51b7-435e-bfe5-8cc5b47d2657)


### Result and Findings

- The presented analysis and visualization provide valuable insights into regional happiness rankings. Notably, Australia and New Zealand emerge as the region with the highest average happiness rank, positioning them at the top of the list. In contrast, Sub-Saharan Africa emerges as the region with the least happiness, reflecting the lowest average happiness rank within the dataset for the year 2015. This comparison underscores the diverse spectrum of well-being across regions, with Australia and New Zealand experiencing the highest happiness levels and Sub-Saharan Africa facing greater challenges in achieving happiness

- The analysis and visualization unveil a compelling pattern, underscoring the significant role of freedom in shaping the happiness scores across various regions. Noteworthy examples include Australia and New Zealand, along with North America, which not only exhibit the highest levels of freedom but also boast the most substantial happiness scores. This correlation implies that a greater degree of freedom positively contributes to higher happiness scores in these regions.Conversely, regions such as Sub-Saharan Africa, Middle East and Northern Africa, and Central and Eastern Europe portray a contrasting picture. These areas experience both limited freedom and some of the lowest happiness scores. This observation suggests that the lack of freedom can potentially lead to lower happiness scores, emphasizing the intricate connection between societal liberties and overall well-being in different regions.

- Based on the analysis and visualization, a clear pattern emerges in the relationship between happiness scores and health (life expectancy). The results from the visualization and analysis table demonstrate a notable correlation: regions with lower happiness scores tend to exhibit lower life expectancies.For instance, Southern Asia and Sub-Saharan Africa, characterized by the lowest happiness scores, also showcase lower life expectancies. Conversely, regions like Australia and New Zealand, Western Europe, and North America, which boast higher average happiness scores, also demonstrate higher life expectancies.This observation suggests a meaningful connection between happiness and health outcomes, with higher happiness scores aligning with better life expectancies. This correlation underscores the intricate interplay between subjective well-being and objective health metrics, highlighting the potential impact of happiness on overall population health.

- This above analysis reveals intriguing patterns in the relationship between trust (government corruption) and happiness scores across different regions. Regions such as Australia and New Zealand, North America, and Western Europe, characterized by higher levels of trust, also exhibit elevated happiness scores, suggesting a positive correlation between trust and well-being.Conversely, regions with lower trust levels, such as Sub-Saharan Africa, tend to have lower happiness scores. This underscores the potential impact of governmental trust on the overall happiness of a region's inhabitants.The overall findings highlight the intricate interplay between trust in government institutions and the subjective well-being of populations across diverse regions.

### Recommendations

1. **Focus on Freedom and Trust:**
   - Given the strong correlation observed between freedom and happiness scores, it is recommended for policymakers to prioritize initiatives that enhance personal freedoms within societies.

2. **Addressing Regional Disparities:**
   - Acknowledging the evident regional variations in happiness scores, policymakers should tailor interventions to address specific challenges faced by regions with lower happiness scores, such as Sub-Saharan Africa and Southern Asia.

3. **Building Trust in Government:**
   - Recognizing the impact of trust in government on overall happiness, efforts to improve transparency, accountability, and governance can contribute positively to the well-being of citizens.

4. **Promoting Social Support and Well-being:**
   - Strengthening social support networks within communities can have a positive impact on happiness. Encouraging social cohesion and community engagement initiatives is recommended.

### Closing Remarks

In conclusion, the World Happiness Exploratory Data Analysis has provided valuable insights into the multifaceted factors influencing happiness across different regions. The findings emphasize the interconnectedness of freedom, trust, and social support with overall happiness. As we navigate the complexities of global well-being, these insights serve as a foundation for informed decision-making and policy formulation.

By prioritizing the enhancement of personal freedoms, fostering trust in government, and addressing regional disparities, societies can move closer to achieving a more harmonious and contented global community. The journey towards greater happiness involves collective efforts, and the data-driven recommendations provided here aim to contribute to the ongoing discourse on fostering well-being and quality of life for all.
