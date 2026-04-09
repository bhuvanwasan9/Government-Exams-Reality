# 📊 India Govt Exams Landscape: Applicants vs. Reality (2019-2024)

**Author:** Bhuvan Wasan | Data Analyst

**Tools Used:** Power BI, Power Query, DAX, Excel/CSV

## 📑 Project Overview

This Power BI dashboard analyzes the highly competitive landscape of Indian Government Examinations (2019-2024). Using datasets from major recruiting bodies like **UPSC, SSC, RRB, IBPS, and UPPRPB**, it uncovers the staggering reality of public sector recruitment. The project highlights immense applicant volumes, significant pre-exam drop-out rates, and hyper-competitive selection rates, offering a data-backed perspective on government job aspirations in India.

## 📸 Dashboard Preview

*(See the dashboard overview below)*

> `![Dashboard Screenshot](Images/Untitled.pdf.jpg)`

## 🎯 Key Objectives

* **Visualize the Gap:** Highlight the vast gap between registered applicants and available vacancies.

* **Metric Calculation:** Calculate accurate selection, appearance, and attrition rates using custom DAX measures.

* **Interactive Exploration:** Allow stakeholders to filter and compare data across years, exam levels, and conducting bodies.

* **Identify Trends:** Uncover year-over-year application trends to understand demographic shifts.

## 🛠️ Data Preparation & Transformation (ETL)

The raw CSV dataset was cleaned and transformed using **Power Query Editor**:

* **Data Validation:** Formatted numerical fields (Applicants, Vacancies, Appeared) as Whole Numbers to prevent aggregation errors.

* **Handling Anomalies:** Standardized missing values and inconsistent naming conventions (e.g., "Railway Recruitment" to "RRB").

* **Feature Engineering:** * Created an `Exam_Level` column to categorize exams ("State Level" vs "Central Level").
  * Added a `Drop_Out_Count` column (`[Total_Applicants] - [Appeared_Candidates]`) to analyze candidate attrition.
  * Extracted a `Year` column from exam dates for time-intelligence reporting.

## 🧮 Data Modeling & DAX Measures

A star-schema data model was established. The following key **DAX measures** were engineered to drive dashboard interactivity:

// --- Core Base Measures ---
Total Applicants = SUM(govt_exams_data[Total_Applicants])
Total Appeared = SUM(govt_exams_data[Appeared_Candidates])
Total Vacancies = SUM(govt_exams_data[Total_Vacancies])
Total Selected = SUM(govt_exams_data[Selected_Candidates])

// --- Analytical & Ratio Measures ---
Appearance Rate % = DIVIDE([Total Appeared], [Total Applicants], 0)

Selection Rate % = DIVIDE([Total Selected], [Total Applicants], 0)

Drop Out Rate % = DIVIDE(([Total Applicants] - [Total Appeared]), [Total Applicants], 0)

## 📈 Dashboard Visualizations

* **Top KPI Cards:** Headline metrics displaying **59M Total Applicants**, **320K Total Vacancies**, **50.61% Appearance Rate**, and a **0.54% Selection Rate**.

* **Area Chart:** *Appeared Candidates and Selection Rate % by Year* tracking trends from 2019 to 2024.

* **Clustered Bar Chart:** *Total Applicants and Total Vacancies by Exam Name* comparing specific high-volume exams (e.g., RRB NTPC, RRB Group D, SSC CGL).

* **Donut Chart:** *Total Applicants by Conducting Body* mapping the share of total applicant volume managed by different bodies.

* **Column Chart:** *Sum of Year by Conducting Body* comparing SSC, UPSC, IBPS, RRB, and UPPRPB.

* **Funnel Summary:** *Total Applicants, Appeared Candidates and Selected Candidates* showing the drop from 59M applied to 30M appeared to nearly 0M selected.

## 💡 Key Insights Discovered

1. **Unprecedented Volume:** A staggering **59 Million** total applicants applied for various exams over the period, competing for a remarkably small pool of just **320K** vacancies.

2. **Conducting Body Dominance:** The Railway Recruitment Board (RRB) handles the largest share of applicants at **48.6%**, followed closely by the Staff Selection Commission (SSC) at **29.86%**.

3. **The "No-Show" Factor:** The overall appearance rate sits at **50.61%**, meaning nearly half of the registered candidates drop out and do not appear on test day.

4. **The 0.5% Reality:** The ultimate selection rate is aggressively competitive, sitting at just **0.54%** of the initial applicant pool across these major exams.

## 📂 Repository Structure

├── Data/
│   └── govt_exams_raw_data.csv       # Dataset used for analysis
├── Dashboard/
│   └── Govt_Exams_Analysis.pbix      # Functional Power BI file
├── Images/
│   └── Untitled.pdf.jpg              # README screenshot
└── README.md                         # Project documentation

## 🚀 How to Use / Interact

1. Clone this repository:

git clone https://github.com/yourusername/india-govt-exams-analysis.git

2. Ensure you have [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) installed.

3. Open `Govt_Exams_Analysis.pbix` in the `Dashboard` folder.

4. Use the slicers to filter by **Year** or **Conducting Body** to dynamically update visuals.

## 🤝 Connect & Feedback

Feel free to explore the dataset and dashboard file. If you found this analysis insightful, let's connect!

* **Author:** Bhuvan Wasan

* **LinkedIn:** https://www.linkedin.com/in/bhuvan-wasan-4546701b7

* **Email:** bhuvanwasan9@gmail.com

*If you like this project, please consider giving this repository a ⭐!*
