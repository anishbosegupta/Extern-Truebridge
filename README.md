# Extern-Truebridge
### README: Asthma Emergency Department Utilization Analysis

## Project Title
**Asthma Emergency Department Utilization**

### Focus: Evesham Township, New Jersey

### Research Question:
**Primary Research Question:**
How do asthma emergency-department visit rates in Evesham Township compare with rates in other municipalities in Burlington County, Camden County, and New Jersey overall?

**Secondary Research Question:**
Which factors, socioeconomic or environmental, appear to be most strongly associated with higher asthma emergency-department utilization, and what implications do these findings have for local public health or planning interventions?

This notebook applies exploratory data analysis (EDA) and statistical methods to examine asthma-related emergency department (ED) utilization across New Jersey municipalities, with a focused case study on Evesham Township.

The analysis demonstrates:
- Descriptive statistics and ranking
- Geographic comparison
- Hypothesis testing
- Risk stratification
- Regression-based expected vs actual analysis

## 2. Introduction: Setting the Stage
This report investigates asthma-related emergency department (ED) utilization in New Jersey, with a particular focus on Evesham Township. Asthma is a chronic respiratory condition that, when poorly controlled, can lead to frequent ED visits, indicating a significant public health burden and potential disparities in healthcare access or environmental exposures. Understanding the factors associated with high ED utilization is crucial for developing targeted public health interventions.

## 3. Data & Methodology: How Was the Analysis Conducted?

### Dataset Overview
The analysis utilized a dataset containing asthma ED utilization rates and various social determinants of health for multiple geographic levels: State, County, and Municipality in New Jersey. The dataset includes variables such as Total Population, Poverty (% Under 2x FPL), Minority %, No Health Insurance %, Traffic (% near heavy traffic), Air Cancer Risk, Air Non-Cancer Risk, Air Quality Index, and Flooding Urban Land Cover.

### Data Cleaning & Preprocessing
- Missing values in `Asthma_ED_Rate_10k` were handled by dropping corresponding rows, ensuring valid analysis at the municipality level.
- Key variables exhibiting right-skewed distributions (`Asthma_ED_Rate_10k`, `Poverty_%_Under_2x`, `Minority_%`, `No_Health_Insurance_%`) were transformed using a square root function to achieve more normal distributions, enhancing their suitability for statistical tests.
- The dataset was subsetted to include only municipality-level data, and specific rows for Evesham Township, Burlington County, Camden County, and New Jersey State were isolated for comparative analysis.

### Methods Used
- **Descriptive Statistics & Ranking**: Municipalities were ranked based on asthma ED rates, and Evesham Township's position was evaluated.
- **Distribution Analysis**: Histograms and boxplots were used to visualize the distributions of key variables before and after transformation, with Evesham Township highlighted.
- **Comparison to Peer Geographies**: Evesham Township's metrics were compared against mean values for Burlington County, Camden County, and New Jersey State.
- **Hypothesis Testing**: One-sample t-tests were performed to determine if Evesham Township's rates for various metrics significantly differed from the means of Burlington and Camden County municipalities.
- **Correlation Analysis**: Pearson correlation coefficients and a heatmap were used to explore relationships between asthma ED rates and socioeconomic/environmental factors.
- **Regression Analysis**: A multiple linear regression model was developed to predict asthma ED rates based on `No_Health_Insurance_%_sqrt` and `Minority_%`.
- **Risk Stratification**: Municipalities were grouped into risk categories using quantile-based approaches for various socioeconomic and environmental factors.

## 4. Key Findings & Visualizations:

### Data Overview & Preparation
- The square root transformation successfully normalized the distributions of `Asthma ED Rate`, `Poverty`, `Minority %`, and `No Health Insurance %`, which were initially right-skewed.

### Descriptive Statistics & Statewide Ranking
- Evesham Township's Asthma ED Visit Rate was 23.80 per 10,000 residents, ranking 42nd out of 53 municipalities (22.6th percentile), indicating a significantly **lower** rate than approximately 77.4% of municipalities in Burlington and Camden Counties.
- Top-ranking municipalities for highest asthma ED rates included Camden City (302.0) and Willingboro Township (132.5).

### Distribution Analysis
- Evesham's asthma ED rate, poverty, and uninsured rates fall in the lower-to-middle range of the transformed distributions, indicating relatively favorable outcomes.
- Environmental factors like traffic and flooding showed zero-inflated distributions, making direct interpretation challenging, though Evesham generally showed moderate-to-low exposure.

### Comparison to Peer Geographies
- Evesham Township's asthma ED rate (23.8) is substantially lower than the average rates for Burlington County (44.02), Camden County (65.16), and New Jersey (not explicitly shown in output but implied to be higher or similar to county averages).
- Across most socioeconomic and environmental metrics, Evesham exhibits values below the mean of both Burlington and Camden Counties.

### Hypothesis Testing (One-Sample T-tests)
- Evesham Township's rates for most metrics (Asthma ED (sqrt), Poverty (sqrt), No Health Insurance (sqrt), Minority % (sqrt), Air Cancer Risk, Air Non Cancer, Air Quality Index, and Flooding Urban Land Cover) were statistically significantly different from the mean of Burlington County municipalities.
- For Camden County, Evesham's rates for most metrics were significantly different, except for `High Traffic Exposure %` and `Flooding Urban Land Cover`.

### Correlation Analysis
- **Strongest Positive Correlations with Asthma ED Rates**: `No_Health_Insurance_%_sqrt` (0.48), `Minority_%_sqrt` (0.47), and `Poverty_%_Under_2x_sqrt` (0.58) showed the most significant positive correlations with transformed asthma ED rates.
- **Intercorrelation among Socioeconomic Factors**: High correlations were observed between poverty, uninsured rates, and minority population, suggesting these factors are intertwined.
- **Weak or Negligible Correlations with Environmental Factors**: Air quality, air cancer risk, air non-cancer risk, and traffic exposure showed surprisingly weak or even slightly negative correlations with asthma ED rates.

### Regression Analysis
- A multiple linear regression model using `No_Health_Insurance_%_sqrt` and `Minority_%` explained 14.2% of the variance in Asthma ED rates (Adjusted R² = 0.106). The model was statistically significant (p=0.024).
- Individual predictors showed mixed significance due to multicollinearity, with `No_Health_Insurance_%_sqrt` approaching significance (p=0.097) and `Minority_%` not being significant (p=0.305).
- The low R² suggests that many unmeasured factors contribute to asthma ED utilization.
- Evesham Township's predicted Asthma ED Rate was approximately 29.86, while its actual rate was 23.80, suggesting the model slightly overestimates its rate given its socioeconomic profile.

### Risk Stratification
- Evesham Township generally falls into lower-risk categories across indicators based on standardized socioeconomic variables.
- An outlier, Riverton Borough, showed high asthma ED rates (106.1) despite having a low composite risk score, warranting further investigation.

## 5. Conclusion & Recommendations:

### Conclusion
Evesham Township consistently demonstrates a favorable profile with lower asthma ED visit rates and lower socioeconomic risk factors compared to many other municipalities in Burlington and Camden Counties and New Jersey overall. The analysis highlights that **socioeconomic factors (uninsured rates, minority population, poverty) are more strongly associated with asthma ED utilization than the environmental factors examined** in this dataset. This suggests that public health interventions aimed at improving healthcare access and addressing social determinants of health may be more impactful in reducing asthma-related ED visits than interventions solely focused on the environmental metrics included here. The modest explanatory power of the regression model indicates the complex, multifactorial nature of asthma ED utilization, emphasizing the need for comprehensive approaches that consider clinical, behavioral, and broader systemic influences.

### Recommendations
1.  **Prioritize Socioeconomic Interventions**: Focus on programs that improve healthcare access, reduce poverty, and support minority communities, as these factors show the strongest links to asthma ED utilization.
2.  **Investigate Healthcare Access**: Explore barriers to primary and preventive asthma care, especially for uninsured populations, as this appears to be a critical driver of ED visits.
3.  **Refine Environmental Data**: If environmental factors are to be further explored, consider more granular or specific measures (e.g., indoor air quality, specific allergen exposures, proximity to industrial sites) that may have a stronger direct impact on asthma exacerbations.
4.  **Community-Specific Deep Dives**: Conduct qualitative research or more detailed analyses in municipalities like Riverton Borough (high asthma, low risk) to understand unique local factors contributing to their asthma ED rates.
5.  **Develop Multifaceted Programs**: Implement integrated public health initiatives that combine social support, healthcare access improvements, and targeted environmental interventions where specific local risks are identified.

## Usage / How to Run
This notebook can be run in Google Colab. Ensure you have the following:
- **Data File**: `asthma_ed_cleaned.csv` should be uploaded to your Colab environment or accessed as specified in the notebook.
- **Dependencies**: The notebook uses `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, `statsmodels`, and `scikit-learn`. These are standard libraries for data analysis in Python and are typically pre-installed or can be installed via `!pip install` commands present in the notebook.

Execute the cells sequentially to reproduce the analysis and visualizations.
