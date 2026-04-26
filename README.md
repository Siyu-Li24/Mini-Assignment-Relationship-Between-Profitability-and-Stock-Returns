# Mini Assignment: Relationship Between Profitability and Stock Returns

**Author:** Siyu Li  
**Student ID:** 2470599  
**Module:** ACC102  

**Product Link / Demo:** [Insert GitHub repository link, notebook link, or demo video link here]

## 1. Problem & User
This project examines whether more profitable firms tend to generate higher stock returns. Profitability is measured using Return on Assets (ROA), while stock performance is measured using annual stock returns constructed from monthly CRSP return data. The main objective is to test whether a simple accounting-based measure can help explain variation in market performance across firms.

The intended users of this project are business students, beginner investors, and entry-level financial analysts who want a clear example of how accounting information and stock market data can be combined to study a practical finance question.

## 2. Data
**Source:** Wharton Research Data Services (WRDS)

The project uses three WRDS datasets:
- **Compustat Fundamentals Annual (`comp.funda`)** for firm-level accounting data
- **CRSP Monthly Stock File (`crsp.msf`)** for monthly stock return data
- **CRSP/Compustat Merged Link Table (`crsp.ccmxpf_linktable`)** for linking accounting identifiers to stock identifiers

**Access date:** 21 April 2026

**Key fields used:**
- `gvkey` — firm identifier from Compustat
- `permno` — stock identifier from CRSP
- `ni` — net income
- `at` — total assets
- `ret` — monthly stock return
- fiscal year and calendar year variables used for matching

**Constructed variables:**
- `roa = ni / at`
- `annual_return` calculated by compounding monthly stock returns within each year

The accounting data and stock return data are merged through the CCM link table using valid link periods, allowing profitability measures to be matched with annual stock returns in the final analysis dataset.

## 3. Methods
The analysis was conducted in Python and followed these main steps:

1. Connect to WRDS and retrieve accounting and market data
2. Download annual accounting data from Compustat
3. Clean the accounting dataset by removing missing values and invalid observations
4. Calculate Return on Assets (ROA) as net income divided by total assets
5. Download monthly stock return data from CRSP
6. Convert monthly returns into annual stock returns through compounding
7. Use the CCM link table to match Compustat firms to CRSP securities
8. Merge the accounting data with annual stock return data to create the final sample
9. Generate descriptive statistics for the key variables
10. Visualize the distributions of ROA and annual stock returns
11. Conduct correlation analysis between profitability and stock returns
12. Produce a scatter plot to inspect the relationship visually
13. Group firms by ROA quartiles to compare stock return patterns across profitability levels
14. Estimate a regression model to test whether ROA is associated with annual stock returns

The project was implemented using Python libraries including `wrds`, `pandas`, `numpy`, `matplotlib`, `seaborn`, and `statsmodels`.

## 4. Key Findings
The analysis shows that profitability and stock returns are positively related, although the relationship is not perfect. Firms with higher ROA generally perform better in terms of annual stock returns than firms with lower ROA.

The descriptive analysis suggests meaningful variation in both profitability and return performance across the sample. The correlation analysis indicates a positive association between ROA and annual stock returns. The scatter plot also supports this pattern, although the data remain widely dispersed, implying that profitability is only one of many factors affecting stock performance.

The quartile comparison further suggests that firms in higher profitability groups tend to achieve stronger return outcomes than firms in lower profitability groups. In addition, the regression analysis provides formal evidence that ROA is positively associated with annual stock returns in this sample.

Overall, the findings suggest that profitability screening may be a useful starting point for evaluating firms, but it should not be treated as a complete explanation of stock performance.

## 5. How to Run
To reproduce this analysis locally:

1. Clone or download this repository
2. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
