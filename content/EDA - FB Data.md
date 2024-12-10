--- title: "EDA Case: Return on Investment in Facebook Ads" subtitle: "MSB 325 - Introduction to Business Analytics (for entrepreneurs)" author: "Connor McCoy**do not skip this**" date: "`r Sys.Date()`" format: # docx: # number-sections: true # number-depth: 2 # colorlinks: true # pdf: # toc: true # number-depth: 2 # number-sections: true # colorlinks: true html: toc: true number-depth: 2 code-fold: false number-sections: true colorlinks: true embed-resources: true editor: visual execute: echo: false ---

\newpage

# Overview

In this case, you will analyze real-world Facebook ad data to uncover insights about ad performance. Imagine you've been engaged by **Alexa** at **Brightwave**, a young e-commerce company founded by Alexa. She is reviewing ad performance data to guide strategic decisions on budget allocation and targeting. Your task is to help her uncover key insights and actionable recommendations.

This analysis is designed to help you:

- Use AI tools to support data analysis and interpretation.
    
- Engage critically with AI outputs, validating and expanding upon them.
    
- Apply insights in practical, decision-making contexts for a client.
    

**Instructions**:

1. **Use AI Extensively**: For each analysis step, use AI to help generate code, interpret results, and suggest further analysis. Practice prompt writing, asking for code, asking follow-up questions for clarity, and validating AI output.
    
2. **Show Your Work**: Document both the code and the AI prompts you use to generate it. This will show your engagement and help build a record of your analytical process.
    
3. **Critically Interpret**: After each analysis step, write an interpretation in your own words. Consider how reliable the AI's interpretation is, what alternative views might exist, and what real-world decisions Alexa could make based on the insights.
    

---

\newpage

# Data

This dataset contains key metrics and calculated fields related to the performance of Facebook ads run by **Brightwave**, a young e-commerce company founded by Alexa. Brightwave is testing multiple ad campaigns to drive brand awareness, generate leads, and boost sales.

The data specifically focuses on the campaign with **Campaign ID 1178**, which is Brightwave’s largest ad campaign in terms of both ad spend and conversions. Alexa chose to run this campaign with significant investment, targeting a wide audience to determine the best approach for reaching potential customers. By analyzing this campaign, Alexa hopes to refine future ad strategies to improve engagement and maximize the return on ad spend (ROAS).

The dataset includes both raw metrics directly downloaded from Facebook Ads Manager and calculated fields that provide insights into ad performance. Below is an explanation of each variable included in the dataset:

## Variables

1. **ad_id**: Unique identifier for each ad in the dataset, used to track and analyze individual ad performance within Campaign ID 1178.
    
2. **brightwave_campaign_id**: Identifier for the campaign within Brightwave’s internal system, where Campaign ID 1178 is the focus of this analysis due to its significant budget and conversion results.
    
3. **fb_campaign_id**: Identifier used by Facebook to track the ad’s campaign across various Facebook platforms.
    
4. **age**: Age group targeted by the ad (e.g., "30-34"), helping Brightwave understand which demographics are most engaged.
    
5. **gender**: Gender targeted by the ad, indicated as "M" for male or "F" for female, allowing analysis of gender-based engagement and conversions.
    
6. **interest**: Interest category targeted by the ad, represented as a numeric code. This helps Alexa analyze which types of interests are associated with better ad performance.
    
7. **Impressions**: The number of times the ad was shown to users, providing insight into the campaign’s reach and visibility on Facebook.
    
8. **Clicks**: The number of times users clicked on the ad, which indicates the ad’s effectiveness in driving interest and engagement.
    
9. **Spent**: The total amount spent on the ad in dollars, reflecting Brightwave’s investment in reaching its target audience.
    
10. **Leads**: Number of users who showed interest in the product or service (e.g., signed up or expressed interest) but did not necessarily make a purchase. Leads are important for tracking initial interest in the brand.
    
11. **Conversions**: Number of users who completed a high-value action, such as a purchase, after clicking on the ad. **This is Brightwave’s primary performance metric**, as it reflects actual sales and revenue generated.
    
12. **CTR (Click-Through Rate)**: The percentage of impressions that resulted in a click. Calculated as `(Clicks / Impressions) * 100`. A higher CTR indicates that the ad content resonates well with the audience.
    
13. **CPC (Cost Per Click)**: Average cost per click on the ad. Calculated as `Spent / Clicks`. This metric shows how cost-efficient the ad is in generating clicks.
    
14. **Lead_Value**: Fixed value per lead, set at 5 dollars to represent the assumed value of each lead. Although not directly generating revenue, leads are valuable for understanding potential future customers.
    
15. **Conversion_Value**: Fixed value per conversion, set at 100 dollars to represent the assumed value of each conversion or purchase. This value is used in calculations to estimate total revenue generated from conversions.
    
16. **Total_Conversion_Value**: Total value generated from conversions (purchases), calculated as `Conversions * Conversion_Value`. This represents the total estimated revenue from Campaign ID 1178’s conversions.
    
17. **CPA (Cost Per Acquisition)**: Average cost per conversion. Calculated as `Spent / Conversions`. CPA provides insight into how much Brightwave spends to generate a single sale or conversion.
    
18. **ROAS (Return on Ad Spend)**: Return on ad spend, showing the revenue generated per dollar spent. Calculated as `(Conversions * Conversion_Value) / Spent`. ROAS is a key metric for understanding the profitability of the ad spend, with higher values indicating a more effective use of budget.
    
19. **CPM (Cost Per Thousand Impressions)**: Cost per thousand impressions, calculated as `(Spent / Impressions) * 1000`. CPM indicates the cost efficiency of reaching the audience in terms of exposure.
    

## Import Data

To begin your analysis, download the dataset CSV file (`fb_ad_data.csv`) provided in Canvas and load it into R. Use AI generated code or the code below or the RStudio interface to import the file and name it `fb_ad_data`:

```
library(tidyverse)
# Replace "path/to/your/file.csv" with the actual path to the downloaded file
fb_ad_data <- read.csv("path/to/your/file.csv")

# Preview the first few rows to ensure it loaded correctly
head(fb_ad_data)
```

Ensure that the file is saved in your working directory, or use the full file path in the `read.csv()` function.

{r} # Copy and paste the generic data import code from above and adapt for your file path or working directory library(tidyverse) read_csv("fb_ad_data.csv")

---

\newpage

# Instructions for Analysis and Submission

1. **Complete this `.qmd` file** by:
    
    - Filling in the code chunks with your EDA code using R and the `tidyverse`.
        
    - Filling in the response sections with your interpretation of the results as prompted in the document.
        
2. **Follow each prompt carefully**: For each question, provide both the code (in the designated code chunk) and a written interpretation (in the designated response section) as outlined in this document.
    
    1. **Document Prompts and Code**: As you use AI, document each prompt and resulting code, along with any changes you make. This demonstrates your engagement and allows you to track what worked well and what needed adjustment.
        
    2. **Emphasize Real-World Relevance**: In each reflection, relate your insights back to Alexa’s decision-making at Brightwave. Consider how these insights could guide Brightwave’s campaigns, budgeting, or audience targeting.
        
3. **Render the file to PDF**:
    
    - Option 1: Render the `.qmd` file to an HTML file first, then convert it to a PDF using your browser's print-to-PDF feature. This option may be the most straightforward as long as it generates a PDF with multiple pages.
        
    - Option 2: Render the `.qmd` file to a Word `.docx` file, then convert it to a PDF. This option seems to be the most reliable but has an extra step.
        
    - Option 3: Render the `.qmd` file directly to a PDF document if you have the necessary tools installed (e.g., LaTeX).
        
4. **Upload your final PDF to Gradescope** through the Canvas assignment:
    
    - Ensure that your PDF is multi-page and fully readable. A single-page PDF will be unreadable in Gradescope.
        
    - Use Gradescope’s interface to label the questions within the PDF, making it easier for grading.
        

---

\newpage

# Case Study: EDA of Facebook Ads

This assignment analyzes the ad campaign data from **BrightWave**, focusing on the company’s largest campaign (Campaign ID 1178). Follow the prompts below to complete your analysis. Answer in the designated code chunks and response sections.

---

## Initial Data Exploration

### AI Prompt(s)

- Use AI to generate initial code for exploring and understanding the data structure. Begin with a prompt like: "Generate R and tidyverse code to provide summary statistics and visualizations for an initial exploration of my dataset."
    
- If you refine your prompts or ask follow-up questions, include each one here in the order you used them, numbering each version (e.g., 1, 2, 3…).
    

> _Copy your AI prompts here:_

1. Initial prompt: ...
    
2. Follow-up prompt: ...
    

### Data Analysis

Begin with a general examination of the data. Use AI-generated code to:

- Generate summary statistics (e.g., mean, median, standard deviation) for each variable.
    
- Create visualizations (e.g., histograms for continuous variables or bar plots for categorical variables) to understand each variable’s distribution.
    

Paste your AI-generated code below, and run it to get a foundational view of the dataset. Make sure your code covers all variables so that you have a complete picture before diving into more specific analyses in later sections.

{r} # AI-Generated Code Example # Use this code chunk to run initial summary statistics and visualizations

### Insights and Recommendations

After viewing the summary statistics and distributions:

- Identify 2-3 variables that look promising for further analysis. Briefly explain why each variable stands out as important or interesting.
    
- Describe any patterns, trends, or anomalies you notice (e.g., skewed distributions, outliers, unusual values).
    
- Consider: What initial strengths or areas for improvement do you observe that Alexa could focus on? For example, if you see high variability in spending, how might Brightwave use this insight to refine ad budget allocation?
    

Write your observations below, and feel free to use AI to help refine your interpretations and suggestions.

> _Write your insights and recommendations here:_

- Insight about key variables: ...
    
- Observation on trends/anomalies: ...
    
- Suggested action for Alexa: ...
    

\newpage

---

## Univariate Analysis for Key Variables

### AI Prompt(s)

Use AI to help generate code for univariate exploration. Start with prompts like:

- "Generate R code to calculate mean, median, standard deviation, and skewness for each of my selected variables."
    
- "Create a histogram and boxplot for [variable] to visualize its distribution and identify potential outliers."
    

> _Copy your AI prompt(s) here:_

1. First AI prompt ...
    

### Data Analysis

Choose 4-6 variables that you believe are central to ad performance, such as `Spent`, `CTR`, or `Conversions.`

> **Note**: Typically, we're interested in identifying both "causal" variables that might drive performance (e.g., Spent, Impressions) and "outcome" variables that measure performance directly (e.g., CTR, Conversions). This will help you choose variables to analyze the factors influencing ad success and evaluate the ad’s effectiveness.

For each selected variable, conduct the following analyses:

- **Summary Statistics**: Calculate mean, median, standard deviation, and skewness for each variable.
    
- **Visualizations**: Use a histogram or boxplot to display the distribution and identify patterns (e.g., symmetry, skewness).
    
- **Outlier Detection**: Identify outliers using boxplots and/or statistical methods (e.g., Z-scores or IQR). Outliers can significantly impact insights and decisions.
    
- **Normality Test** (optional): Since some statistical tests assume normal distribution, test for normality using Q-Q plots or the Shapiro-Wilk test for each variable. If non-normal, note this in your interpretation, as it may impact analysis later.
    

{r} # AI-Generated Code Example # Use this code chunk for univariate statistics and visualizations for chosen variables

### Insights and Recommendations

- For each variable, summarize what the data suggests (e.g., distribution shape, presence of outliers, central tendency).
    
- Use AI to assist in interpreting results. Ask questions like, "How might this skewness affect ad performance?" or "What could high variance imply about ad spend patterns?"
    
- Consider any real-world recommendations for Alexa based on each variable’s insights. For example, if Spent has significant outliers, suggest ways to adjust or monitor the budget to reduce variance.
    

> _Write your insights and recommendations here_:

- First insight on key variables (e.g., observations on skewness, variance, and how these may impact ad performance)
    

---

\newpage

## Bivariate Analysis for Key Numeric Relationships

### AI Prompt(s)

Use AI to generate R and tidyverse code for your bivariate analysis using scatter plots, trend lines, and correlation coefficients for key numeric relationships. Use prompts like:

- "Generate R code to create a scatter plot with a trend line for [variable 1] vs. [variable 2]."
    
- "Calculate the Pearson or Spearman correlation for [variable 1] and [variable 2]."
    

> _Copy your AI prompt(s) here_:

1. First AI prompt ...
    

### Data Analysis

1. **Identify Core Numeric-Numeric Relationships**:
    

- Select 2–3 pairs of variables you believe have a meaningful relationship (e.g., `Spent` vs. `Conversions`, `CTR` vs. `Impressions`).
    
- **Visualization Each Pair**: Use scatter plots with trend lines to examine the direction and strength of these relationships.
    
- **Calculate Correlations**: Calculate Pearson or Spearman correlation coefficients, as appropriate, to assess the strength of the relationships.
    

2. **Statistical Testing for Numeric-Categorical Relationships (Verification)**:
    

- If your _univariate EDA suggests differences_ in a numeric variable (e.g., `CTR`) across categories (e.g., `age` or `gender`), use a **t-test** or **ANOVA** to confirm these differences.
    
- Instructions:
    
    - use a t-test for comparing means of a numeric variable between two categories (e.g., male vs. female).
        
    - use ANOVA for comparing means of a numeric variable across multiple categories (e.g., different age groups).
        
    
    If you observe notable differences between groups, report these insights to Alexa, as they could inform targeted marketing strategies.
    

3. **Chi-Square Testing for Categorical-Categorical Relationships**:
    

- If you observe an association between two categorical variables (e.g., `gender` and `age` groups), use a chi-square test to evaluate whether these variables are independent.
    

{r} # AI-Generated Code Example # Use this code chunk for bivariate analysis on variable pairs

### Insights and Recommendations

1. **Interpret Direction and Strength of Relationships**: For each variable pair:
    

- Describe the direction (positive or negative) and strength of the relationship.
    
- Reflect on what the relationship might imply for ad performance. For example, a strong positive correlation between `Spent` and `Conversions` might indicate that increased spending directly drives more conversions.
    

2. **Recommendations Based on Relationships**:
    

- Based on these relationships, describe potential actions Alexa could take. For instance, if higher `Spent` reliably leads to increased `Conversions`, suggest that Alexa consider allocating more budget to specific ads.
    
- Consider using AI to explore scenarios or "what-if" questions, such as "If `CTR` increases, how might `ROAS` change?"
    

> _Write your insights and recommendations here:_

1. First insight and/or recommendation on numeric relationships ...
    

---

\newpage

## Demographic Comparisons

### AI Prompt(s)

Use AI to generate R and tidyverse code for your demographic comparisons. In this section, you'll examine how key numeric relationships vary across demographic categories. Provide the AI prompt(s) you used to generate code for this analysis, numbering multiple iterations clearly.

> _Copy your AI prompts here:_

1. First AI prompt …
    

### Data Analysis

1. **Visualize Relationships Across Demographic Categories**:
    
    - Choose key variable pairs previously analyzed (e.g., `Spent` vs. `Conversions`, `CTR` vs. `Impressions`) and examine how these relationships differ across demographic categories such as `age` or `gender.`
        
    - **Use Color in Scatter Plots**: For each pair, create scatter plots with trend lines, using color to represent different demographic categories (e.g., separate lines or color points by `age` groups or `gender`).
        
    - **Group Comparison Visualizations**: Use box plots or faceted scatter plots to visually assess differences in key numeric variables (e.g., `CTR`, `Conversions`) across categories.
        
2. **Statistical Testing for Demographic Differences**:
    
    - Conduct statistical tests to confirm whether differences observed across demographic categories are statistically significant.
        
    - Use t-tests or ANOVA for comparing numeric variables across demographic groups.
        
    - Use chi-square tests to examine relationships between categorical demographic variables, if applicable.
        

{r} # AI-Generated Code Example # Use this code chunk to conduct demographic comparisons and visualizations

### Insights and Recommendations

1. **Interpret Demographic Differences**:
    
    - Summarize any differences you observe in the relationships across demographic categories (e.g., how the Spent vs. Conversions relationship differs across age groups or gender).
        
    - Discuss how demographic categories influence these key relationships. For example, if a stronger relationship between Spent and Conversions is observed in certain age groups, this might suggest that targeting these groups could yield better returns.
        
2. **Actionable Recommendations**:
    
    - Based on demographic insights, suggest targeted strategies for Alexa at Brightwave. For instance, if younger demographics (e.g., ages 18–24) show higher conversions for the same ad spend, recommend focusing future ads on these demographics.
        
    - Use AI to brainstorm further recommendations or scenario testing (e.g., "What might happen if Alexa increased spending on ads targeted at specific age groups?").
        

> _Write your insights and recommendations here:_

1. First insight and/or recommendation based on demographic analysis …
    

---

\newpage

## Final Synthesis and Recommendations

### AI Prompt(s)

Use AI to help synthesize your findings and support your recommendations. Provide AI prompt(s) that assist with generating high-level summaries, insights, and practical recommendations. Include any prompts used to refine or validate these recommendations.

> _Copy your AI prompts here:_

1. First AI prompt …
    

### Key Insights

1. **Summarize Core Findings**:
    
    - Reflect on the most impactful insights from your univariate, bivariate, and demographic analyses. Identify 3-5 key findings that reveal the drivers and performance metrics of Brightwave’s Facebook ads.
        
    - For each insight, note any patterns, trends, or differences across demographic categories that could inform ad strategy and audience targeting.
        

### Optional Summary Visualizations (with Code)

Use this code chunk to create summary visualizations (if helpful), such as an overview chart or other plot that distills key findings from your analyses into a final, cohesive visual. This is optional but can be a helpful summary tool for both you and Alexa.

{r} # Optional Code Chunk for Summary Visualizations or Tables # If you wish, create any final summary visualizations or tables here to illustrate key insights or highlight patterns for your recommendations. # This step is optional and intended only for students who feel additional visuals could enhance their final synthesis.

2. **Generate Data-Driven Recommendations**:
    
    - Using your core insights, generate actionable recommendations for Alexa at Brightwave, focusing on areas like ad strategy, targeting demographics, and budget allocation.
        
    - Consider the implications of each recommendation, including potential benefits and risks. If appropriate, use AI to help expand or validate these recommendations.
        

### Reflection and Practical Considerations

1. **Refine Recommendations**:
    
    - Reflect on the practical application of your recommendations. Consider whether they are feasible, any associated costs, and how they align with Brightwave’s overall marketing goals.
        
    - Address any limitations of the analysis, and consider how Alexa could further validate these findings—such as through A/B testing, controlled experiments, or additional data collection.
        
2. **Identify Future Data Needs**:
    
    - Highlight any areas where additional data could deepen the analysis or confirm your recommendations. Suggest specific data sources or metrics that Alexa could track in future campaigns.
        

> Write your reflections and practical recommendations here:

1. **First key insight and recommendation**: Describe the insight and related recommendation, including potential action steps and any anticipated impact on ad performance.
    
2. **Risks and validation considerations**: Discuss any risks associated with the recommendation and suggest ways Alexa might validate this strategy.
    

---

\newpage

# Submission Checklist

- **Code Completeness**: Ensure all code sections are filled out and run without errors.
    
- **Response Quality**: Ensure all response sections are complete and provide actionable insights.
    
- **Rendering**: Render the document to PDF and verify that all sections are readable.
    
- **Upload**: Submit the PDF to Gradescope.
    

---