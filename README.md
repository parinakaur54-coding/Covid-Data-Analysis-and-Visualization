# COVID-19 Data Analysis & Visualization

## 1. Title

# COVID-19 Data Analysis Using SQL & Tableau

An exploratory data analysis project examining the global impact of COVID-19 through **SQL data analysis and interactive Tableau visualizations**.

The project analyzes COVID-19 cases, deaths, infection rates, and population impact across different countries and continents to identify major trends and provide data-driven insights.

**Tools Used:**
`SQL Server` · `Microsoft Excel` · `Tableau`

**Interactive Dashboard:**
[View the COVID-19 Tableau Dashboard](https://public.tableau.com/app/profile/pareendeep.kaur/viz/Covidanalysis_17862434967380/Dashboard1?utm_source=chatgpt.com)

---

## 2. Executive Summary

The COVID-19 pandemic had a significant global impact, affecting populations, healthcare systems, and economies worldwide. This project analyzes COVID-19 data to understand the scale and distribution of the pandemic.

Using **SQL Server**, the raw COVID-19 dataset was queried and transformed into meaningful metrics, including:

* Total COVID-19 cases
* Total COVID-19 deaths
* Global death percentage
* Total deaths by location
* Highest infection count by country
* Percentage of population infected
* Infection trends over time

The resulting datasets were exported to Excel and used to create an interactive **Tableau dashboard** for visual analysis.

The analysis provides an overview of how COVID-19 affected different regions and identifies countries with particularly high infection rates and death counts.

---

## 3. Business Problem

The COVID-19 pandemic generated a massive amount of data, making it difficult to quickly understand the overall scale and differences in impact between countries.

The key questions addressed in this project are:

* What was the total number of COVID-19 cases and deaths globally?
* Which locations experienced the highest number of deaths?
* Which countries had the highest infection counts?
* What percentage of a country's population became infected?
* How did COVID-19 infections change over time?
* Which continents and regions experienced the greatest impact?

### Objective

The objective of this project is to transform raw COVID-19 data into **clear, meaningful, and interactive insights** that can help users understand the global impact of the pandemic and compare its effects across different locations.

---

## 4. Methodology

### Data Analysis Workflow

```text
COVID-19 Dataset
       ↓
   SQL Server
       ↓
Data Cleaning & Transformation
       ↓
SQL Queries
       ↓
Export Results to Excel
       ↓
Tableau
       ↓
Interactive Dashboard
       ↓
Insights & Recommendations
```

### Step 1 — Data Preparation

The COVID-19 dataset was stored and analyzed using **SQL Server**.

The analysis focused primarily on the `CovidDeaths` table and relevant fields such as:

* `location`
* `continent`
* `date`
* `population`
* `new_cases`
* `new_deaths`
* `total_cases`
* `total_deaths`

### Step 2 — Global COVID-19 Statistics

The first query calculates the overall number of cases, deaths, and death percentage.

```sql
SELECT 
    SUM(new_cases) AS total_cases,
    SUM(CAST(new_deaths AS INT)) AS total_deaths,
    SUM(CAST(new_deaths AS INT)) / SUM(new_cases) * 100 AS DeathPercentage
FROM PortfolioProject..CovidDeaths
WHERE continent IS NOT NULL;
```

### Step 3 — Death Count by Location

The second query identifies locations with the highest total death counts while excluding aggregate entities such as the World, European Union, and International.

```sql
SELECT 
    location,
    SUM(CAST(new_deaths AS INT)) AS TotalDeathCount
FROM PortfolioProject..CovidDeaths
WHERE continent IS NULL
    AND location NOT IN ('World', 'European Union', 'International')
GROUP BY location
ORDER BY TotalDeathCount DESC;
```

### Step 4 — Infection Rate by Country

The third query identifies the highest infection count and percentage of population infected for each location.

```sql
SELECT 
    Location,
    Population,
    MAX(total_cases) AS HighestInfectionCount,
    MAX((total_cases / population)) * 100 AS PercentPopulationInfected
FROM PortfolioProject..CovidDeaths
GROUP BY Location, Population
ORDER BY PercentPopulationInfected DESC;
```

### Step 5 — Infection Trends Over Time

The fourth query analyzes infection levels over time by location and date.

```sql
SELECT 
    Location,
    Population,
    date,
    MAX(total_cases) AS HighestInfectionCount,
    MAX((total_cases / population)) * 100 AS PercentPopulationInfected
FROM PortfolioProject..CovidDeaths
GROUP BY Location, Population, date
ORDER BY PercentPopulationInfected DESC;
```

### Step 6 — Tableau Visualization

The processed SQL results were exported to Excel and connected to Tableau to create interactive visualizations.

The dashboard allows users to explore COVID-19 statistics and compare the pandemic's impact across different regions and countries.

---

## 5. Skills

### Technical Skills

* **SQL**

  * Data aggregation
  * `SUM()`
  * `MAX()`
  * `GROUP BY`
  * `ORDER BY`
  * Filtering with `WHERE`
  * Data type conversion using `CAST()`
  * Calculated metrics
* **Tableau**

  * Dashboard development
  * Data visualization
  * Bar charts
  * KPI displays
  * Geographic analysis
  * Interactive filtering
* **Microsoft Excel**

  * Data storage
  * Data preparation
  * Dataset transfer between SQL and Tableau

### Analytical Skills

* Exploratory Data Analysis
* Data Cleaning
* Data Transformation
* KPI Analysis
* Trend Analysis
* Comparative Analysis
* Data Visualization
* Business Insight Generation

---

## 6. Results & Business Recommendation

### Key Results

The analysis provides several important insights into the global impact of COVID-19.

#### Global Impact

The dashboard calculates approximately:

| Metric                  |         Result |
| ----------------------- | -------------: |
| Total Cases             | 150.57 Million |
| Total Deaths            |   3.18 Million |
| Global Death Percentage |            ~2% |

These figures demonstrate the significant scale of the pandemic and its impact on populations worldwide.

### Deaths by Continent

The analysis shows substantial differences in total death counts between continents. Europe and North America represent some of the regions with the highest recorded death counts in the analyzed dataset.

### Infection Rate

The percentage of population infected provides a more meaningful comparison between countries than total case counts alone.

A country with a smaller population may have fewer total cases but still experience a very high proportion of its population becoming infected.

### Business Recommendations

Based on the analysis, organizations and policymakers should:

1. **Monitor infection rates rather than relying only on total case counts.**
   Population-adjusted metrics provide better comparisons between countries.

2. **Use data visualization for faster decision-making.**
   Interactive dashboards can help decision-makers identify trends and high-impact regions quickly.

3. **Strengthen health data infrastructure.**
   Centralized and reliable data collection enables better monitoring during future pandemics.

4. **Focus resources on high-impact regions.**
   Death counts and infection percentages can help identify areas requiring greater healthcare and public-health support.

5. **Monitor trends over time.**
   Historical infection data can help identify changes in pandemic patterns and support future preparedness.

---

## 7. Next Steps

Future improvements to this project could include:

* Adding **COVID-19 vaccination data**
* Analyzing **vaccination rates vs. death rates**
* Adding **hospitalization and ICU data**
* Creating more detailed **country-level comparisons**
* Adding interactive **date filters**
* Analyzing relationships between **population, infection rate, and mortality**
* Incorporating additional demographic and socioeconomic indicators
* Automating the SQL-to-Tableau data pipeline
* Expanding the dashboard with additional KPIs and predictive analysis

### Dashboard

[Explore the Interactive Tableau Dashboard →](https://public.tableau.com/app/profile/pareendeep.kaur/viz/Covidanalysis_17862434967380/Dashboard1?utm_source=chatgpt.com)

---


### Tools & Technologies

`SQL Server` `Microsoft Excel` `Tableau` `Data Analysis` `Data Visualization`

---

**Author:** Pareendeep Kaur
**Project:** COVID-19 Data Analysis
**Dashboard:** [Tableau Public](https://public.tableau.com/app/profile/pareendeep.kaur/viz/Covidanalysis_17862434967380/Dashboard1?utm_source=chatgpt.com)
