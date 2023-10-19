![image](https://github.com/beto1810/IBM_HR_Analytic/assets/101379141/1a50adfb-e413-46c5-96f5-41b72ede39ee)# 🛒 IBM - Human Resources - Analysis Report


 ![image](https://github.com/beto1810/IBM_HR_Analytic/assets/101379141/717ea9fa-bd89-493c-8aa7-2a4ac5dc684e)


# :books: Table of Contents <!-- omit in toc -->

- [:briefcase: Business Case and Requirement](#briefcase-business-case-and-requirement)
- [:bookmark_tabs:Example Datasets](#bookmark_tabsexample-datasets)
- [A. Analysis](#a-data-exploration-and-cleansing)
- [B. Building Machine Learning Model](#b-analysis)

- [📃 What can you practice with this case study?](#what-can-you-practice-with-this-case-study)

---

# :briefcase: Business Case and Requirement


You are a Data Analyst working for a Human Resources Department. You are tasked with preparing a presentation to present answers for the attrition of employees in Company. And Building the Machine Learning Model to predict the employee who has high possibility to attrit from company.

❔ The presentation should include at a minimum the following information: 
- Basic Analysis for reasons why Employees have willing to leave company and ways to improve it.
- The predict Model for attrition in the future.

---

# :bookmark_tabs:Example Datasets

### ✔ HR_Analytics
Provide information to analyze and building model
- Age: Age of Employee.
- Attrition: False for not attrition, True for attrition.
- BusinessTravel: How often the employee make business trip.
- DailyRate: Salary Rate by day
- Department: Department of Employee
- DistanceFromHome: Distance From Home to Workplace (km)
- Education: Educational Level - 1 'Below College', 2 'College', 3 'Bachelor', 4 'Master', 5 'Doctor'
- Education Field: Major Field of Employee
- Employee Count: Dummy Variable
- Employee Number
- Environment Satisfaction: 1 'Low', 2 'Medium', 3 'High', 4 'Very High'.
- Gender
- HourlyRate: Salary Rate by Hour
- Jobinvolvement: 1 'Low', 2 'Medium', 3 'High', 4 'Very High'.
- JobLevel: 1 'Low', 2 'Medium', 3 'High', 4 'Very High'.
- JobRole
- MarialStatus: Status of Marriage
- MonthlyIncome: Income by Month
- MonthlyRate
- NumcompaniesWorked: How many company that employees have worked since start working
- Over18: Y - Yes & N - No
- OverTime: True & False
- PercentSalaryHike: The percent of increasing salary annualy
- PerformanceRating: Performance Rate of Employee
- RelationshipSatisfaction: 1 'Low', 2 'Medium', 3 'High', 4 'Very High'.
- StandardHours: Standard Working Hour for Labor
- StockOptionLevel: 0 - Not Choose, 1-3 : Choose with different conversion rate.
- TotalWorking Years: Working Experiences in Year
- TrainingTimesLastYears
- WorLifeBalance: 1 'Low', 2 'Medium', 3 'High', 4 'Very High'.
- YearsAtCompany: Working Experience by year at current company
- YearsInCurrentRole: How Long that employees standed in current position in year
- YearSinceLastPromotion
- YearsWithCurrManager: How Long that employees cooperate with current manager in year


<details><summary> 👆🏼 Click to expand HR Analytics Dataset </summary>

<div align="center">

**Table: HR Analytics** 

<div align="center">
First 10 rows

|"Age|	Attrition|	BusinessTravel|	DailyRate|	Department|	DistanceFromHome|	Education|	EducationField|	EmployeeCount|	EmployeeNumber|	EnvironmentSatisfaction|	Gender|	HourlyRate|	JobInvolvement|	JobLevel|	JobRole|	JobSatisfaction|	MaritalStatus|	MonthlyIncome|	MonthlyRate|	NumCompaniesWorked|	Over18|	OverTime|	PercentSalaryHike|	PerformanceRating|	RelationshipSatisfaction|	StandardHours|	StockOptionLevel|	TotalWorkingYears|	TrainingTimesLastYear|	WorkLifeBalance|	YearsAtCompany|	YearsInCurrentRole|	YearsSinceLastPromotion|	YearsWithCurrManager"|
|:----|:-----|:----|:----|:----|:----|:----|:----|:----|:-----|:----|:----|:----|:----|:----|:----|:----|:-----|:----|:----|:----|:----|:----|:----|:----|:-----|:----|:----|:----|:----|:----|:----|:----|:----|:----|
|"41	|Yes|	Travel_Rarely|	1102|	Sales|	1|	2|	Life Sciences|	1	|1	|2	|Female|	94	|3	|2	|Sales Executive	|4	|Single	|5993	|19479	|8	|Y	|Yes	|11	|3	|1	|80	|0	|8	|0	|1	|6	|4	|0	|5"|
|"49	|No|	Travel_Frequently|	279	| Research & Development|	8 |	1 |	Life Sciences|	1|	2|	3	|Male|	61	|2	|2	|Research Scientist|	2	|Married|	5130	|24907	|1|	Y	|No|	23	|4	|4|	80|	1	|10|	3|	3|	10|	7|	1|	7"|
|"37	|Yes|	Travel_Rarely|	1373	| Research & Development	|2	| 2	|Other|	1	|4	|4	|Male	|92	|2	|1	|Laboratory Technician	|3	|Single	|2090	|2396	|6	|Y	|Yes	|15	|3	|2	|80	|0	|7	|3	|3	|0	|0	|0	|0"|
|"33	|No|	Travel_Frequently|	1392	| Research & Development|	3|	4	|Life Sciences|	1	|5	|4	|Female|	56|	3	|1	|Research Scientist|	3	|Married|	2909|	23159|	1	|Y	|Yes|	11|	3|	3|	80|	0|	8|	3|	3|	8|	7|	3|	0"|
|"27	|No|	Travel_Rarely	|591	|Research & Development	|2	| 1	|Medical|	1	|7	|1	|Male	|40	|3	|1	|Laboratory Technician	|2	|Married	|3468	|16632	|9	|Y	|No	|12	|3	|4	|80	|1	|6	|3	|3	|2	|2	|2	|2"|
|"32	|No|	Travel_Frequently|	1005|	Research & Development|	2|	2	|Life Sciences|	1	|8	|4	|Male	|79	|3	|1	|Laboratory Technician	|4|	Single|	3068	|11864|	0	|Y	|No	|13	|3	|3	|80	|0	|8	|2|	2	|7	|7	|3	|6"|
|"59	|No|	Travel_Rarely	|1324	|Research & Development	|3	| 3	|Medical|	1	|10	|3	|Female	|81	|4	|1	|Laboratory Technician	|1	|Married	|2670	|9964	|4	|Y	|Yes	|20	|4	|1	|80	|3	|12	|3	|2	|1	|0	|0	|0"|
|"30	|No|	Travel_Rarely	|1358	|Research & Development	|24	| 1	|Life Sciences|	1	|11	|4	|Male	|67	|3	|1	|Laboratory Technician	|3	|Divorced|	2693	|13335|	1	|Y	|No|	22|	4|	2|	80|	1|	1|	2|	3|	1|	0|	0|	0"|
|"38	|No|	Travel_Frequently|	216|	Research & Development|	23 |	|3	Life Sciences|	1	|12	|4	|Male	|44	|2	|3	|Manufacturing Director	|3	|Single	|9526	|8787	|0	|Y	|No	|21	|4	|2	|80	|0	|10	|2	|3	|9	|7	|1	|8"|
|"36	|No|	Travel_Rarely	|1299|	Research & Development	|27 |	3	|Medical|	1	|13|	3|	Male|	94|	3|	2|	Healthcare Representative|	3	|Married|	5237|	16577|	6|	Y	|No|	13|	3|	2|	80|	2|	17|	3|	2|	7|	7|	7|	7"|


</div>
</div>

</details>

---

### ✔ HR employee data  
Provide Addition information about Employee and Emloyee Number 
- EmployeeNumber: 
- Employee_name

<details><summary> 👆 Click to expand HR employee Dataset </summary>

<div align="center">

**Table:  HR employee dataset** 

<div align="center">
First 10 rows


|EmployeeNumber|Employee_name|
|:----|:-----|
1	|Barak Sali|
2	|Mumin Yusha|
4	|Cordia M Knopp|
5	|Burton C Jin|
7	|Femi Grek|
8	|Hugh N Chavira|
10	|Lucius C Moorhead|
11	|Deane I Keown|
12	|Joannie E Wolters|
13	|Christene L Mccaleb|

  
</div>
</div>

</details>

---

### ✔ Retrenchment dataset
Provide information of upcomming Employee's Retrenchment 

- Employee name: 
- Will be retrenched: 0 - No, 1-Yes

<details><summary> 👆 Click to expand Retrenchment dataset </summary>

<div align="center">

**Table: order_payments_dataset** 

<div align="center">
First 10 rows

|Employee name|Will be retrenched|
|:----|:-----|
Abbey Schindler|	0|
Abe J Macleod|	0|
Abe Morales|	0|
Abe X Paro|	0|
Abram Q Keffer|	0|
Abram S Manrique|	0|
Adalberto W Creek|	1|
Adam B Katzer|	0|
Adelaide L Harrop|	1|
Adele M Burnam|	0|



</div>
</div>

</details>

---

### ✔ promomtion dataset 
Provide information about upcomming Employee's promotion
- Employee name: 
- Due for promotion: 1 - Waiting for promotion 

<details><summary> 👆 Click to expand promomtion Dataset </summary>

<div align="center">

**Table: products_dataset** 

<div align="center">
First 10 rows

|Employee name|Due for promotion|
|:----|:-----|
Adelaide L Harrop	|1|
Aiko Blossom	|1|
Alexis Q Grose	|1|
Aliza X Sammons	|1|
America V Lobel	|1|
Amiee Z Chaffins	|1|
Andrew Detweiler	|1|
Brendon E Mone	|1|
Buck H Rancourt	|1|
Candelaria Zajicek	|1|

</div>
</div>

</details>

---

Basicly, we have 4 dataset but only HR Analytics Data - Dataset would be used for analyze and building model for this project. With 3 dataset - retrenchment, promotion and employee data, it would be examined for building a big Relational Database which Primary key is Employee Number 

---


# A. [Data Analysis](#)



# B. [Predict Machine Learning Model](#)


---

# 🧾 What can you practice with this case study?
- Python
  - pandas, numpy,matplotlib,seaborn.
  - cleaning, check Null values, transforming.
 
  - import, save csv file. 
- POWER BI
  - Visualize
  - Analyze
  - Measure, DAX, etc
  - Import CSV File and Transform data
