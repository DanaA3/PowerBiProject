#  AI Impact on Jobs 2030: Workforce Vulnerability & Strategic Upskilling

An interactive, multi-page Microsoft Power BI analytics suite analyzing the transformative impact of Artificial Intelligence on global employment markets heading into 2030.

---

##  Executive Summary
This project evaluates workforce risk exposure, compensation patterns, demand scores, and targeted mitigation strategies across global employment markets. Using star-schema data modeling and custom DAX measures, the report provides actionable intelligence for enterprise leaders and policy makers.

---

##  Dataset Details & Data Preprocessing

* **Source Platform:** Kaggle (`AI_Impact_on_Jobs_2030.csv`)
* **Raw Data Volume:** 3,000 employee records across 20 raw attributes.
* **Processed Data Architecture:** Star Schema consisting of:
  * `Fact_Employees` (773 curated records with 20 analytical fields).
  * `Bridge_Skills` (Normalized dimension table mapping many-to-many skill distributions per employee).

###  Data Cleaning & Pipeline Transformations
1. **Dimensional Normalization:** Extracted multi-valued string lists from `Required_Skills` into a dedicated `Bridge_Skills` table to enable granular skill-gap filtering.
2. **Feature Engineering:** Derived `Salary_Category` to evaluate high-income vs. baseline salary distribution across international markets.
3. **Data Quality & Refinement:** Standardized field header formats (`Employee_ID` → `EmployeeID`) and removed redundant non-correlated entries for dashboard query optimization.
4. **Custom DAX Layer:** Formulated measures for `Avg AI Risk`, `Upskilling Rate %`, `Demand Score Formatting`, and `Net Outlook Score`.

---

### Key Metrics & High-Level Findings

* **Widespread Exposure:** Average AI replacement risk sits at 51.16%, with 49.68% of analyzed roles requiring immediate upskilling.
* **Education Vulnerability:** Highest upskilling demand occurs at the PhD level (54.55%), proving high education levels do not guarantee immunity from AI automation.
* **AI Tool Synergy:** Moderate (3.55 / 5.0) and High (3.54 / 5.0) AI tool adoption yields consistently higher performance scores than Low usage (3.45 / 5.0).
* **Macro Net Outlook:** Net Outlook Score averages -33.39, balancing expected job growth (17.78%) against baseline replacement risk (51.16%).

---

##  Dashboard Page Breakdowns

### 1. Executive Overview
Focuses on macro-level metrics, industry distribution, and country compensation trends.
* **KPI Panel:** Employee Count (773), Avg Salary ($124.73K), Avg AI Risk (51.16%), Upskilling Rate (49.68%), Net Outlook Score (-33.39).
* **Visuals:** Industry Employee Distribution Bar Chart & Country Salary Category Matrix.

### 2. Risk Landscape Analysis
Maps role vulnerabilities against future growth and demand drivers.
* **Visuals:** Future Demand Matrix Table (Conditional Formatting), Risk vs. Job Growth Scatter Plot, and Hierarchical Decomposition Tree.

### 3. Strategic Mitigation & Upskilling Plan
Shifts narrative toward actionable solutions and tool adoption impacts.
* **Visuals:** Upskilling Demand by Education Level & Performance Score by AI Tool Adoption Level.

---

##  Key DAX Measures Implemented
* **Avg AI Risk:** `AVERAGE(Fact_Employees[AI_Replacement_Risk])`
* **Net Outlook Score:** `AVERAGE(Fact_Employees[Job_Growth_2030]) - (AVERAGE(Fact_Employees[AI_Replacement_Risk]) * 100)`
* **Demand Score Formatting:** Dynamic `SWITCH(TRUE(), ...)` color allocation for high/low future demand scores.

---

##  Conclusion
While over 51% of analyzed positions face significant AI replacement risk by 2030, automation threats are heavily offset by upskilling programs and tool adoption. Proactive training in high-demand roles transforms automation risk into productivity gains, establishing long-term workforce sustainability.
