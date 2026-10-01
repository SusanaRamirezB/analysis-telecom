# analysis-telecom. ConnectaTel

## Project Overview ##

This project analyzes customer behavior for ConnectaTel, a
telecommunications company operating in Latin America. The analysis uses
customer, plan, and usage data recorded through 2024 to understand
how customers use mobile calling and messaging services, identify
data-quality issues and unusual usage patterns, and create customer
segments based on age and usage.

The main business goal is to generate actionable insights that can
support **customer retention, customer segmentation, and optimization of
the current plan offering.** 

## Project structure ##

├── Project-ConnectaTel.ipynb

├── README.md

└── datasets/

    ├── plans.csv

    ├── users_latam.csv

    └── usage.csv

## Datasets ##
The project uses three datasets:

**plans.csv** plan information, including monthly price,
included messages, included GB, included minutes, and additional
usage costs.

**users_latam.csv** customer information, including user ID,
age, city, registration date, plan, and churn date.

**usage.csv** historical customer activity, including calls
and text messages, dates, call duration, and message length.

The notebook loads the files from:

plans = pd.read_csv('/datasets/plans.csv')

users = pd.read_csv('/datasets/users_latam.csv')

usage = pd.read_csv('/datasets/usage.csv')

**Note:** if the datasets are stored elsewhere, update these paths before running
the notebook.

## Analysis ##

**1. Data loading and initial exploration**

The three datasets are loaded with Pandas and inspected using .head()
and .info() to understand their structure, columns, data types, and
completeness.

**2. Data quality assessment**

The project checks for:

- Missing values and their proportions.

- Invalid and sentinel values.

- Relevant categorical values.

- Numerical distributions.

- Date formats and dates outside the analysis period.

**Note:** detected issues include invalid age values (-999), invalid city values
(?), future registration dates, and missing values in usage fields.

**3. Data Cleaning**

The notebook applies the following rules:

- Replaces the -999 sentinel in age with the median age.

- Replaces ? in city with pd.NA.

- Marks registration dates after December 31, 2024 as missing.

**Note:** evaluates missing duration and length values according to
interaction type, leaving structurally missing values as null
rather than imputing them indiscriminately.

**4. Customer usage profile**

Usage data is aggregated by user_id to create:

- cant_mensajes - total messages.

- cant_llamadas - total calls.

- cant_minutos_llamada - total call duration.

**Note.** these metrics are combined with customer information to **create a
customer-level profile.** 

**5. Statistical analysis and visualization**

Descriptive statistics and visualizations are used to analyze:

- Customer age.

- Number of messages.

- Number of calls.

- Total call minutes.

- Differences in usage distributions by plan.

**Note: Histograms** are used to examine distributions and boxplots to identify
extreme observations.

**6. Outlier detection**

Outliers are identified using the Interquartile Range (IQR) method.
Upper-end outliers are found in:

- cant_mensajes

- cant_llamadas

- cant_minutos_llamada

**Note:** they are not automatically removed because high usage may **represent
genuine customer behavior and can provide useful business insights.**

**7. Customer segmentation**

Two segmentation approaches are created.

**Usage segmentation**

- Bajo uso - fewer than 5 calls and fewer than 5 messages.

- Uso medio - fewer than 10 calls and fewer than 10 messages,
provided the customer is not already classified as low usage.

- Alto uso - all remaining cases.

**Age segmentation**

- Joven - age below 30.

- Adulto - age below 60.

- Adulto Mayor - remaining cases.

**Note:** The segments are visualized using count plots.

## Key business findings ##

The analysis identifies adults as the largest age segment, followed
by older adults and young customers.

For usage, medium-use customers form the largest segment, while
high-use customers are a smaller group with potentially differentiated
needs.

The analysis also identifies unusually high levels of messaging,
calling, and call duration. These observations should be reviewed rather
than automatically deleted because they may represent legitimate
high-consumption customers or data-quality issues.

The main business opportunity identified is to move from a general plan
offering toward a **more behavior-based customer offering,**
differentiating plans and benefits according to actual usage patterns.

## Main recommendations ##

1. **Create differentiated offers based on actual usage levels,** with
alternatives for low-, medium-, and high-use customers.

2. **Offer upgrades or additional benefits to high-use customers**
whose consumption suggests a need for greater capacity.

3. **Develop retention strategies for medium-use customers,** the
largest usage segment.

4. **Combine age, usage, plan, and churn information** to create more
targeted retention and migration strategies.

5. **Improve data quality and incorporate additional business
variables,** particularly mobile-data consumption, revenue,
additional charges, and profitability.

## How to run the Notebook ##

**GitHub**

1. Open the repository containing the project.

**https://github.com/SusanaRamirezB/analysis-telecom/blob/main/S7%20Project-ConnectaTel.ipynb**

2. Open Project-ConnectaTel.ipynb.

3. Review the notebook directly in GitHub or open it in an interactive
environment such as Google Colab.

4. Make sure the three CSV datasets are available before executing the
notebook.

**Google Colab**

1. Open Project-ConnectaTel.ipynb in Google Colab.

**https://colab.research.google.com/drive/16cf8QCoWD_lY6s7p8iB6cwfOBCXa76hY**

2. Make sure the datasets are available in the expected location.

3. If necessary, update the CSV paths in the data-loading section.

4. Run the notebook cells sequentially from top to bottom.

## Reproduction ##

1. Obtain plans.csv, users_latam.csv, and usage.csv.

2. Place the files in the folder expected by the notebook or update the
file paths.

3. Open Project-ConnectaTel.ipynb in Jupyter Notebook, JupyterLab, or
Google Colab.

4. Ensure the required libraries are installed:pandas, numpy, seaborn and matplotlib.

5. Run the notebook sequentially.

6. Review the data-quality checks, usage aggregation, descriptive
statistics, visualizations, outlier analysis, customer segmentation,
and executive recommendations.

## Tools ##

- Python 3

- Pandas

- NumPy

- Seaborn

- Matplotlib

- Jupyter Notebook / Google Colab

## Project workflow ##

→ Data cleaning 
→ Exploratory data analysis 
→ Usage profiling 
→ Outlier detection 
→ Customer segmentation 
→ Business insights 
→ Recommendations
