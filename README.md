# 2022 Heart Health Indicators: Power BI Analysis

A Power BI report exploring physical activity, age, sleep, sex, and state-level differences in self-reported health outcomes from a cleaned subset of the 2022 Behavioral Risk Factor Surveillance System (BRFSS) data.

## Project files

- [`SEBONTIMAHNAZPROJECT.pbix`](SEBONTIMAHNAZPROJECT.pbix) — Power BI report with the project description, data preparation notes, visuals, and discussion pages.
- [`heartdataset.xlsx`](heartdataset.xlsx) — the cleaned data used for the analysis. The workbook has 210,084 rows and 27 columns.

Open the `.pbix` file in Power BI Desktop to explore the report. The report contains an embedded data model. If you refresh it, the source path may need to be updated to a locally downloaded copy of the original `heart_2022_with_nans.csv` from Kaggle. `heartdataset.xlsx` is the supplied cleaned analysis table for inspection; it is not guaranteed to replace the Power Query source directly.

## Data and preparation

The starting file was `heart_2022_with_nans.csv` from the [Indicators of Heart Disease (2022 Update) dataset on Kaggle](https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease), based on the [CDC's 2022 BRFSS survey](https://www.cdc.gov/brfss/annual_data/annual_2022.html). The supplied starting CSV has 445,132 rows and 40 columns. The cleaned workbook has 210,084 rows and 27 columns.

As documented in the report, preparation included removing unused columns such as `ECigaretteUsage`, height, and weight; excluding records with missing values used in the analysis; adding an `ID` column; shortening age group labels; simplifying some category values; and changing data types and column order. The workbook also contains a `SleepHoursCategory` field. The retained rows have unique IDs and no blank cells in the 27 retained columns. The report does not specify every intermediate filter or a complete executable Power Query recipe, so the cleaned workbook is the supplied analysis dataset. The large reduction in rows is relevant when interpreting results.

## Questions explored

1. How do physical activity and reported health outcomes differ?
2. How do selected conditions vary by sex and age?
3. How does reported prior heart attack vary by age group?
4. How do sleep hours relate to reported health outcomes?
5. How do state-level counts and health measures compare?
6. How do sleep and reported prior heart attack vary by state?

## Selected results

In the cleaned data, 163,234 respondents (77.7%) reported being physically active and 46,850 (22.3%) reported being inactive. The supplied DAX measures `HeartDiseaseRateActive` and `HeartDiseaseRateInactive` count `HadHeartAttack = "Yes"` within each activity group and divide by the group's row count. They produce 7,249 / 163,234 = 4.4% for active respondents and 4,224 / 46,850 = 9.0% for inactive respondents. Thus, for this comparison, the measure names refer specifically to **reported prior heart attack**, not every type of heart disease.

A depressive disorder was reported by 30,143 of 163,234 active respondents (18.5%) and 12,347 of 46,850 inactive respondents (26.4%). Reported prior heart attack increased across age groups in both activity groups, with the highest rates in the 80+ group. These are descriptive associations within the cleaned sample. They do not establish causation or represent weighted population prevalence.

## Method and interpretation

The report uses Power BI visualizations and DAX measures for descriptive analysis. The published percentages above are unweighted row-based rates in the cleaned workbook. BRFSS has a complex survey design and official population estimates require appropriate survey weights and methods. The cleaned subset excludes many original records, and these exclusions may affect comparisons. Interpret the findings as exploratory results for this project dataset.

## Author

Sebonti Mahnaz — Business Analytics and Information Management, University of Delaware.
