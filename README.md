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
- Created a **100k-row synthetic dataset** using Excel.
**STEP 1**File contains Excel data into 3 relational tables.
A.Customers Table
CustomerID
Name
Age
Phone
Email
Location

B.Policies Table
PolicyID (new unique ID)
CustomerID (foreign key)
InsuranceType
SpecificInsuranceCategory
PolicyStartDate
PolicyEndDate
RenewalDate
PremiumAmount

C.Claims Table
ClaimID (new unique ID)
PolicyID (foreign key)
ClaimStatus
ClaimAmount (randomized realistic values depending on policy type)
ClaimDate (within policy period)

**STEP 2**
CreateD Relationships in (Model View) based on CustomerID & PolicyID.
From Table	   Column	       To Table	  Column	       Relationship Type
Customers	    CustomerID	   Policies	  CustomerID	   One-to-Many
Policies	     PolicyID	     Claims	    PolicyID	     One-to-Many 
  **Customers → Policies → Claims**
Power BI me jab hum multiple tables (jaise Customers, Policies, Claims) use karte hain,
to unke beech connection (relationship) banana padta hai — taaki data ek dusre se link ho sake.

**Created Create Key Measures (DAX)**
Go to Modeling → New Measure, and add these:

Total Premium = SUM(Policies[PremiumAmount])
Total Claims = SUM(Claims[ClaimAmount])
Claim Settlement Rate = 
DIVIDE(
    COUNTROWS(FILTER(Claims, Claims[ClaimStatus] = "Claim Settled")),
    COUNTROWS(Claims)
)

Avg Premium = AVERAGE(Policies[PremiumAmount])
Claim Ratio = DIVIDE([Total Claims], [Total Premium])

Customer Count = COUNTROWS(Customers)
Active Policies = 
COUNTROWS(FILTER(Policies, Policies[PolicyEndDate] > TODAY()))  

For Male Customers:
Male Customers = 
CALCULATE(
    COUNTROWS(Customers),
    Customers[Gender] = "Male"
)

For Female Customers:
Female Customers = 
CALCULATE(
    COUNTROWS(Customers),
    Customers[Gender] = "Female"
)

% Male Customers = 
DIVIDE(
    [Male Customers],
    [Customer Count]
)
DAX
Copy code
% Female Customers = 
DIVIDE(
    [Female Customers],
    [Customer Count]
)

Customer Count = COUNTROWS(Customers)

Male Customers = 
CALCULATE(
    COUNTROWS(Customers),
    Customers[Gender] = "Male"
)

Female Customers = 
CALCULATE(
    COUNTROWS(Customers),
    Customers[Gender] = "Female"
)

% Male Customers = DIVIDE([Male Customers], [Customer Count])
% Female Customers = DIVIDE([Female Customers], [Customer Count])

**STEP 3**
🏠 Dashboard Page 1 – Overview
Visual Type	                          Fields	                                          Purpose
Card	                                 Total Premium	                                   Shows overall premium collected
Card	                                 Total Claims	                                    Shows total claim amount
Card	                                 Claim Settlement Rate	                           Shows how many claims were settled
Card	                                 Active Policies	                                 Shows active policy count
Donut Chart	                          InsuranceType (Policies) + Total Premium	        Share of premium by product
Clustered                             Column Chart	Location (Customers) + Total        Premium	Premiums by city
Bar Chart	                            ClaimStatus (Claims) + ClaimAmount	              Claim distribution by status

🚗 Dashboard Page 2 – Product Insights
Visual	                               Fields	                                                   Insight
Table                                	InsuranceType, SpecificInsuranceCategory, Avg Premium	    Compare avg premiums by subcategory
Line Chart	                           PolicyStartDate (Month) + Total Premium	                  Premium trend over time
Matrix	                               InsuranceType vs ClaimStatus + ClaimAmount	               Product-wise claim distribution


👥 Dashboard Page 3 – Customer Insights
Visual	                               Fields	                                                   Insight
Histogram	                            Age (Customers) + Count of Customers	                     Age distribution
Bar                                   Location + Avg Premium	                                   Which city pays higher premiums
Table	                                Name, Age, Location, PremiumAmount, ClaimStatus	          Drill-down data

**STEP4**
Add slicers for Interactivity.
InsuranceType
ClaimStatus
  
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

