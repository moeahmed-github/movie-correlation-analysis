# Movie Correlation Analysis: Understanding the Financial Success Drivers in Cinema

## Project Background

This analysis explores a dataset of 7,668 films released between 1980 and 2020, sourced from IMDb and Box Office data. As a data analyst examining the film industry's economics, I investigated what factors correlate most strongly with a movie's gross revenue performance. The entertainment industry invests billions annually in film production, and understanding which variables drive box office success is critical for studios, investors, and producers making strategic decisions about resource allocation.

The film industry operates on a high-risk, high-reward model where production budgets can range from thousands to hundreds of millions of dollars. Studios need data-driven insights to understand not just what makes a successful film, but what quantifiable factors can predict financial performance before significant capital is deployed.

**Insights and recommendations are provided on the following key areas:**

- **Budget vs. Gross Revenue Correlation**: The relationship between production investment and box office returns
- **Voting & Popularity Metrics**: How audience engagement indicators correlate with financial success
- **Genre & Rating Impact**: Analysis of content characteristics and their relationship to revenue
- **Company & Production Factors**: The influence of production companies and other categorical variables on gross earnings

---

## Data Structure & Initial Checks

The movie dataset consists of a single table with 7,668 records and 15 primary columns. The data structure is as follows:

**Movie Dataset (7,668 rows)**
- **Identifiers**: name (movie title)
- **Classification**: rating (MPAA rating), genre, country
- **Temporal**: year, released (date)
- **Performance Metrics**: score (IMDb rating), votes, gross (box office earnings)
- **Production Details**: budget, director, writer, star, company, runtime (minutes)

**Data Quality Observations:**
- Budget data: 28% missing values (imputed as 0 for analysis)
- Gross revenue: 2% missing values (imputed as 0 for analysis)
- Rating: 1% missing values
- All other fields: <1% missing data
- Data types were corrected (budget and gross converted from float64 to int64)
- Year extraction was performed from the 'released' field for accuracy

---

## Executive Summary

### Overview of Findings

The analysis reveals that **budget is the strongest predictor of box office success**, with a Pearson correlation coefficient of 0.74 with gross revenue. However, **votes (audience engagement) also shows substantial correlation at 0.63**, suggesting that audience popularity—independent of production scale—plays a critical role in financial performance. Genre shows a notable negative correlation with budget (-0.36), indicating that certain genres systematically receive different levels of investment, which has implications for risk-adjusted return strategies.

**Key Takeaway for Studio Executives**: While higher budgets strongly correlate with higher gross revenues, the relationship is not deterministic. Studios should balance large-budget tentpole releases with attention to audience engagement factors and genre positioning to optimize portfolio returns.

![image alt](https://github.com/moeahmed-github/movie-correlation-analysis/blob/d29ca9e4632f4ae6d938cd130ed59ffd1e8d6a32/images/Plot%20The%20Budget%20vs%20Gross%20Using%20Seaborn.webp)

---

## Insights Deep Dive

### Category 1: Budget & Revenue Relationship

**Main Insight 1:** Budget demonstrates the strongest correlation with gross revenue at 0.74, indicating that production investment is the single most important quantifiable factor in predicting box office performance. The relationship appears linear across most budget ranges, with films in the $200M+ range showing the highest gross earnings potential.

**Main Insight 2:** While the correlation is strong, significant variance exists around the regression line. Many high-budget films underperform expectations while some modest-budget films achieve outsized returns, suggesting that budget alone does not guarantee success.

**Main Insight 3:** The top-grossing films in the dataset (Avatar, Avengers: Endgame, Titanic) all feature budgets exceeding $200M, confirming that blockbuster financial performance typically requires blockbuster investment. However, risk also scales with budget.

**Main Insight 4:** The genre-budget negative correlation (-0.36) reveals that certain genres (likely action/adventure) receive systematically higher budgets while others (likely horror/comedy) operate on leaner budgets, presenting different risk/reward profiles.

![image alt](https://github.com/moeahmed-github/movie-correlation-analysis/blob/d29ca9e4632f4ae6d938cd130ed59ffd1e8d6a32/images/Scatter%20Plot%20With%20Budget%20vs%20Gross.webp)

---

### Category 2: Audience Engagement Indicators

**Main Insight 1:** The 'votes' variable (representing number of IMDb user ratings) shows a 0.63 correlation with gross revenue, making it the second-strongest predictor after budget. This suggests that audience engagement and word-of-mouth significantly impact financial performance.

**Main Insight 2:** Votes correlate with budget at 0.44, indicating that higher-budget films generate more audience engagement, but the relationship is not proportional—suggesting that marketing, franchise recognition, and content quality also drive engagement.

**Main Insight 3:** The score (IMDb rating) shows moderate correlation with gross (0.19) and stronger correlation with votes (0.41), indicating that critical/audience quality assessments contribute to engagement but don't directly drive revenue at the same magnitude as other factors.

**Main Insight 4:** Runtime shows weak correlation with gross (0.25) but stronger correlation with score (0.40), suggesting that longer films may offer more satisfying experiences without necessarily translating to higher box office returns.

![image alt](https://github.com/moeahmed-github/movie-correlation-analysis/blob/d29ca9e4632f4ae6d938cd130ed59ffd1e8d6a32/images/Correlation%20matrix%20for%20numeric%20columns.webp)

---

### Category 3: Temporal & Industry Evolution

**Main Insight 1:** Year shows moderate positive correlation with both budget (0.33) and gross (0.26), reflecting industry-wide trends of budget inflation and box office growth over the 1980-2020 period. This suggests the need for inflation-adjusted analyses in future work.

**Main Insight 2:** The year-votes correlation (0.22) indicates increasing audience engagement over time, possibly reflecting the growth of online rating platforms and digital marketing's influence on audience behavior.

**Main Insight 3:** Year shows negative correlation with genre (-0.08), which may indicate shifting genre preferences over the four-decade span, with certain genres becoming more or less prominent in production slates.

**Main Insight 4:** The temporal trends suggest that analyzing ROI (return on investment) would be more valuable than raw gross figures, as both costs and revenues have inflated over time.

![image alt](https://github.com/moeahmed-github/movie-correlation-analysis/blob/d29ca9e4632f4ae6d938cd130ed59ffd1e8d6a32/images/Heatmap%20of%20the%20Pearson%20correlation%20matrix.webp)

---

### Category 4: Categorical Variables & Production Factors

**Main Insight 1:** When categorical variables (company, director, writer, star, genre, rating, country) are numerically encoded, the correlation matrix reveals that company shows modest correlation with gross (0.15), suggesting that certain production studios systematically achieve better results.

**Main Insight 2:** Genre shows the strongest categorical impact, with negative correlations to both budget (-0.36) and gross (-0.24), indicating that genre is a major determinant of both investment level and financial outcome. Action/adventure films likely dominate high-budget, high-gross categories.

**Main Insight 3:** Rating (MPAA classification) shows weak correlations across all metrics, suggesting that PG-13 vs R ratings do not systematically predict financial performance after accounting for other factors.

**Main Insight 4:** Director, writer, and star show minimal correlation with gross revenue when analyzed across all films, suggesting that "star power" may be overrated as a general predictor, though specific individuals may have outsized impact not captured in aggregate correlation analysis.

---

## Recommendations

Based on the insights and findings above, I would recommend **studio executives and production decision-makers** consider the following:

**Budget Allocation Strategy**: Given the strong budget-gross correlation (0.74), studios should maintain a portfolio approach with tentpole high-budget releases balanced against mid-budget films. The variance around the regression line suggests thorough pre-production analysis and risk assessment beyond budget considerations alone.

**Audience Engagement Metrics**: The strong votes-gross correlation (0.63) indicates that marketing strategies focused on driving early audience engagement (opening weekend buzz, social media campaigns, advance screenings) should be prioritized alongside production quality investments.

**Genre-Specific Investment Models**: The genre-budget negative correlation (-0.36) suggests analyzing ROI by genre rather than absolute gross. Horror and thriller genres may offer attractive risk-adjusted returns with lower capital requirements, while action films require massive budgets for competitive positioning.

**Data-Driven Greenlight Processes**: Incorporate quantitative correlation analysis into greenlight decisions. Projects should be evaluated not just on creative merit but on how their characteristics (genre, budget range, talent) align with historical success patterns in the correlation data.

**Expand Analysis to ROI Metrics**: Future analysis should calculate return on investment (gross/budget) as the primary success metric rather than raw gross revenue. This would provide more actionable insights for capital allocation decisions and risk management.

---

## Assumptions and Caveats

Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

**Assumption 1**: Missing budget values (28% of dataset) were imputed as $0 rather than excluded or estimated. This approach was chosen to preserve sample size but may underrepresent the true budget-gross correlation strength, as many low-budget films likely had budgets that weren't recorded rather than truly zero budgets.

**Assumption 2**: Missing gross revenue values (2% of dataset) were imputed as $0, which may include films with unreported earnings or limited releases. This could introduce bias by treating commercial failures and unreported successes identically.

**Assumption 3**: All financial figures are in nominal terms without inflation adjustment. The 40-year span (1980-2020) means that budget and gross figures are not directly comparable across time periods, which impacts the year-correlation interpretations.

**Assumption 4**: The dataset appears to focus on English-language or Hollywood productions, as evidenced by country distribution. Correlation findings may not generalize to international film markets with different economic models (Bollywood, European cinema, etc.).

**Assumption 5**: Correlation does not imply causation. While budget strongly correlates with gross, this doesn't prove that increasing budget causes higher revenue. Confounding factors (franchise recognition, star power, marketing spend, release timing) likely influence both variables.

**Assumption 6**: The categorical encoding approach (converting text to numeric codes) allows for correlation calculation but assumes ordinal relationships that may not exist. For example, alphabetically coded genre or company names create artificial numeric patterns without meaningful quantitative interpretation.

---

##  Contact & Collaboration
Hi! My name is Mohamed Ahmed.
- 💼 LinkedIn: linkedin.com/in/moe-ahmed-hersi
- Open to feedback, collaboration, and data analytics opportunities!

---

##  Acknowledgments

- Special thanks to **Alex**, also known as **Alex The Analyst** for providing clear, practical guidance on SQL data exploration techniques and demonstrating how to structure professional data analytics projects. His teaching approach helped shape the methodology and best practices applied throughout this analysis.
