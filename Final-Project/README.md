# How Vehicle Weight Affects Fuel Efficiency

## Problem and research question
**How does a car's weight affect its fuel efficiency (miles per gallon)?** MPG measures driving distance per gallon. Understanding its relationship with vehicle weight provides a useful example of data analysis, though this project does not test causation.

## Data and license
- Analyzed CSV: https://raw.githubusercontent.com/mwaskom/seaborn-data/master/mpg.csv
- Dataset hosting: https://github.com/mwaskom/seaborn-data
- Original source: UCI Auto MPG, https://archive.ics.uci.edu/dataset/9/auto+mpg
- **License listed by UCI:** Creative Commons Attribution 4.0 International (CC BY 4.0): https://creativecommons.org/licenses/by/4.0/
- Attribution: *Auto MPG dataset*, UCI Machine Learning Repository; analyzed using the version hosted by seaborn-data. Seaborn warns that hosted samples may differ from original datasets.
- Fields studied: `mpg`, `weight`, `model_year`, `cylinders`. No personally identifying information.

## Documented cleaning log
- Imported **398** rows and **9** columns.
- Checked missing values: **6 missing `horsepower` values**; **0 missing** `mpg` or `weight` values.
- Checked exact duplicates: **0**.
- Converted `mpg` and `weight` to numeric with invalid values treated as missing.
- Removed **0** rows lacking essential MPG/weight measurements; removed **0** exact duplicates.
- **398** rows remained. The six missing horsepower values were retained because horsepower was not part of the analysis.

## Methods and results
The notebook calculated descriptive statistics, a Pearson correlation, and a least-squares linear trend.

| Metric | Verified result |
|---|---:|
| Cars analyzed | 398 |
| Average MPG | 23.51 |
| Median MPG | 23.00 |
| Average vehicle weight | 2,970.42 lb |
| Pearson correlation (weight, MPG) | -0.832 |
| Fitted MPG difference per additional 1,000 lb | -7.68 MPG |

### Chart 1: Weight versus MPG
![Scatter plot of vehicle weight and MPG with fitted line](charts/01_weight_vs_mpg.png)

The downward point pattern and **r = -0.832** show a strong negative association: heavier vehicles generally have lower MPG in this sample. The fitted line estimates a difference of about **7.68 MPG per 1,000 lb**; this is not a prediction of what would happen if a car's weight were experimentally changed.

### Chart 2: MPG by model year
![Line chart of mean MPG by model year](charts/02_average_mpg_by_year.png)

Average MPG was **17.69** in model year **1970** and **31.71** in **1982**. The changes were not perfectly steady: the dataset reaches **33.70 MPG in 1980**. Year-related differences might coincide with weight, design, or other factors.

### Chart 3: MPG by cylinder count
![Bar chart of mean MPG by cylinder count](charts/03_average_mpg_by_cylinders.png)

Four-cylinder cars averaged **29.29 MPG** (n=204), six-cylinder cars **19.99 MPG** (n=84), and eight-cylinder cars **14.96 MPG** (n=103). The 3- and 5-cylinder groups contained only **4 and 3** cars, so avoid interpreting their averages too strongly. These are descriptive group differences, not causal estimates.

## Main conclusion
**Answer:** Heavier cars tended to have poorer fuel efficiency in this historical dataset. This conclusion is supported by the scatter plot, a strong negative correlation, and a downward fitted line. The other two charts offer descriptive context, not evidence that weight alone determines MPG.

## Limitations
These data represent cars from **1970–1982**, not today's vehicle fleet. Observational data cannot isolate the impact of weight because engine size, cylinders, year, and other design differences may be related. Results describe the sampled CSV and should not be generalized mechanically to all cars.

## 
