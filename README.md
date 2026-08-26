#  AI Impact on Jobs 2030: Workforce Vulnerability & Strategic Upskilling

An interactive, multi-page Microsoft Power BI analytics suite analyzing the transformative impact of Artificial Intelligence on global employment markets heading into 2030.

---

##  Executive Summary
This project evaluates workforce risk exposure, compensation patterns, demand scores, and targeted mitigation strategies across global employment markets. Using star-schema data modeling and custom DAX measures, the report provides actionable intelligence for enterprise leaders and policy makers.

---

##  Dataset Details & Data Architecture
* **Dataset:** `AI_Impact_on_Jobs_2030.csv` (Kaggle)
* **Data Volume:** 773 records across 20 attributes
* **Model Structure:** Star Schema (`Fact_Employees` fact table linked to `Bridge_Skills` dimension table)
* **Core Attributes:** `AI_Replacement_Risk`, `Job_Growth_2030`, `Average_Salary_USD`, `Future_Demand_Score`, `Automation_Level`, `Upskilling_Needed`, `AI_Tool_Usage`, `Performance_Score`, `Education_Level`

---

##  Key Metrics & High-Level Findings
* **Widespread Exposure:** Average AI replacement risk sits at **51.16%**, with **49.68%** of analyzed roles requiring immediate upskilling.
* **Education Vulnerability:** Highest upskilling demand occurs at the **PhD level (54.55%)**, proving that high education levels do not guarantee immunity from AI automation.
* **AI Tool Synergy:** Employees utilizing AI tools at Moderate to High levels achieve consistently higher performance scores (**3.54 - 3.55 / 5.0**) compared to Low-usage peers (**3.45 / 5.0**).

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
