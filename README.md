# Acko-insurance-dashboard
Acko Insurance — Power BI Dashboard.

**About** Acko General Insurance is India’s first fully digital insurance company, built with a tech-first approach to make insurance simple, fast, and accessible for everyone. Founded in 2016, Acko operates on a digital-only model, allowing customers to purchase policies, file claims, and renew plans entirely online—without paperwork, agents, or physical branches.

**Overview**  
Interactive Power BI dashboard built on synthetic insurance data inspired by Acko.  
Includes analytics for product performance, claims, customer insights and renewals.

📁Repository Contents
-data— Synthetic datasets (Excel)
-pbix— Power BI Desktop file: `Acko_Insurance_Dashboard.pbix`
-images— Dashboard screenshots for quick preview.

🧩 Steps Involved in the Project

1. **Data Generation & Preparation**
- Created a **100k-row synthetic dataset** using Python & Excel.
- Added fields: CustomerID, Name, Gender, Age, City, Product Type, Premium, Claim Status, Claim Amount, Claim Date, Policy Dates.
- Extended dataset with: Age Groups, Renewal Indicators, and Policy Segments.

2. **Power BI Data Modeling**
- Designed a **star-schema**:  
  **Customers → Policies → Claims**
- Created relationships based on CustomerID & PolicyID.
- Applied Power Query transformations.

**Dashboard Design**
- Used consistent color themes
- Navigation buttons & slicers
- Clear KPI cards and charts
- Custom formatting for ₹ currency & %
- Clean, BI-ready layout across 3 pages

🧩Features
- Overview KPIs: Total Premiums, Total Claims, Claim Settlement Rate, Active Policies  
- Product Analysis: Premiums, Claims, Avg Premiums by product  
- Customer Insights: Age distribution, Gender analysis, Location trends  
- DAX measures, star schema model (Customers → Policies → Claims), dynamic slicers

🛠️Tech & Tools
- Microsoft Excel (data preparation)  
- Power BI Desktop (visualization & modeling)  
- DAX & Power Query (calculations & transformations)

