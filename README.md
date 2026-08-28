# AI Impact on Jobs 2030: Workforce Vulnerability & Strategic Upskilling

An interactive, multi-page Microsoft Power BI analytics suite analyzing the transformative impact of Artificial Intelligence on global employment markets heading into 2030.

## Executive Summary

This project evaluates workforce risk exposure, compensation patterns, demand scores, and targeted mitigation strategies across global employment markets. Using star-schema data modeling and custom DAX measures, the report provides actionable intelligence for enterprise leaders and policy makers.

## Dataset Details & Data Preprocessing

- **Source Platform:** Kaggle (`AI_Impact_on_Jobs_2030.csv`)
- **Raw Data Volume:** 3,000 employee records across 20 raw attributes.
- **Processed Data Architecture:** Star Schema consisting of:
  - `Fact_Employees` — 773 sampled records with 20 analytical fields, drawn from the raw 3,000-record dataset for report performance during interactive slicing/filtering.
  - `Bridge_Skills` — Normalized dimension table (4,638 rows) mapping the many-to-many relationship between employees and their listed skills, extracted from the `Required_Skills` column.

## Data Cleaning & Pipeline Transformations

1. **Dimensional Normalization:** Extracted multi-valued string lists from `Required_Skills` into a dedicated `Bridge_Skills` table to enable granular skill-gap filtering.
2. **Feature Engineering:** Derived `Salary_Category` to evaluate high-income vs. baseline salary distribution across international markets.
3. **Data Quality & Refinement:** Standardized field header formats (`Employee_ID` → `EmployeeID`) for consistency across the star schema.
4. **Custom DAX Layer:** Formulated measures for `Avg AI Risk`, `Upskilling Rate %`, `Demand Score Conditional Formatting`, and `Net Outlook Score`.

## Key Metrics & High-Level Findings

- **Widespread Exposure:** Average AI replacement risk sits at 51.16%, with 49.68% of analyzed roles requiring immediate upskilling.
- **Education Vulnerability:** Highest upskilling demand occurs at the PhD level (54.55%), proving high education levels do not guarantee immunity from AI automation.
- **AI Tool Synergy:** Moderate (3.55 / 5.0) and High (3.54 / 5.0) AI tool adoption yields consistently higher performance scores than Low usage (3.45 / 5.0).
- **Macro Net Outlook:** Net Outlook Score averages -33.39, balancing expected job growth (17.78%) against baseline replacement risk (51.16%).

## Dashboard Page Breakdowns

### 1. Executive Overview
Focuses on macro-level metrics, industry distribution, and country compensation trends.

- **KPI Panel:** Employee Count (773), Avg Salary ($124.73K), Avg AI Risk (51.16%), Upskilling Rate (49.68%), Net Outlook Score (-33.39).
- **Visuals:** Industry Employee Distribution Bar Chart & **Average Salary by Country Bar Chart** (sorted descending, replacing an earlier salary-category view that didn't differentiate between countries).

### 2. Risk Landscape Analysis
Maps role vulnerabilities against future growth and demand drivers.

- **Visuals:** **"Avg Future Demand Score by Job Title & Automation Level"** table (explicitly titled to distinguish it from AI replacement risk — it reflects Future_Demand_Score, not AI_Replacement_Risk, conditionally color-coded by Automation Level), Risk vs. Job Growth Scatter Plot (bubble size = Avg Salary), and a Hierarchical Decomposition Tree of AI-replaceable roles by Education Level, Industry, and Company Size.

### 3. Strategic Mitigation & Upskilling Plan
Shifts narrative toward actionable solutions, tool adoption impacts, and flexible work exposure.

- **Visuals:**
  - Upskilling Demand by Education Level Bar Chart.
  - Performance Score by AI Tool Adoption Level Bar Chart.
  - Upskilling Rate % & Avg AI Risk by Remote Work Line Chart: Demonstrates that fully remote roles face the highest replacement risk (52.64%) and upskilling demand (51.82%), while non-remote positions experience lower exposure (48.90% risk / 46.03% upskilling rate).
  - **Top 10 Skills Across Workforce Bar Chart** (new): Built from the `Bridge_Skills` table, this surfaces the most common skills held across employees, with an interactive slicer to filter down to only employees flagged as needing upskilling — directly connecting the skills dimension to the mitigation narrative instead of leaving it unused in the data model.

## Key DAX Measures Implemented

- **Avg AI Risk:** `AVERAGE(Fact_Employees[AI_Replacement_Risk])`
- **Net Outlook Score:** `AVERAGE(Fact_Employees[Job_Growth_2030]) - (AVERAGE(Fact_Employees[AI_Replacement_Risk]) * 100)`
- **Demand Score Conditional Formatting:** Dynamic `SWITCH(TRUE(), ...)` color allocation applied to the Future Demand Score table for high/low visual emphasis.

## How to Reproduce

- **Tools used:** Microsoft Power BI Desktop (August 2026 release or later), Excel/openpyxl for the star-schema staging file.
- **Files in this repo:**
  - `AI_Jobs_2030.pbix` — the full interactive report (open directly in Power BI Desktop; no external data connection required, data is embedded).
  - `AI_Jobs_2030_Model.xlsx` — staging workbook containing the `Fact_Employees` and `Bridge_Skills` tables as loaded into the model.
  - `AI_Impact_on_Jobs_2030.csv` — original raw dataset (3,000 records) as sourced from Kaggle.
  - `/screenshots` — static PNG exports of all three report pages, for anyone viewing this repo without Power BI Desktop installed.
- **Data source:** [Kaggle — AI Impact on Jobs 2030 dataset](#) *( https://www.kaggle.com/datasets/muhammadwaqas023/ai-impact-in-future-on-jobs-market-in-2030/data)*.
- **To open the report:** clone the repo, open `AI_Jobs_2030.pbix` in Power BI Desktop, and use **Home → Refresh** if you want to re-point it at a local copy of the CSV rather than the embedded snapshot.

## Limitations & Next Steps

The `Fact_Employees` table is a 773-record sample drawn from the original 3,000-row dataset for report responsiveness, not the result of a data-quality filter. The raw data had no nulls or duplicates, so findings should be read as directional rather than a full-population statistic, and a natural next step is re-running the model against the complete 3,000 records to confirm the risk and salary patterns hold at scale. The underlying Kaggle dataset also appears to be synthetically generated rather than sourced from real labor-market surveys, which is appropriate for a portfolio/methodology demonstration but means the specific percentages (e.g., 51.16% AI risk) shouldn't be cited as real-world labor statistics. Future iterations could incorporate a genuine longitudinal or survey-based labor dataset (e.g., BLS, OECD, or WEF Future of Jobs data) to validate whether the AI-risk-vs-remote-work and AI-risk-vs-education patterns observed here replicate against real employment data.

## Conclusion

While over 51% of analyzed positions face significant AI replacement risk by 2030, automation threats are heavily offset by upskilling programs and tool adoption. Proactive training in high-demand roles transforms automation risk into productivity gains, establishing long-term workforce sustainability.
