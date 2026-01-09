# SQL for Beginners  
**Learning Microsoft Transact-SQL through Real-World Data Cleaning**

This repository demonstrates how to use Microsoft SQL Server (T-SQL) to **identify, analyze, and correct data quality issues** in an HR dataset.  
The project is designed for beginners who want hands-on experience with **SELECT, DISTINCT, UPDATE, validation queries, and data consistency checks**.

---

## 📘 Dataset Used
**Table Name:** `HRDataset`  
The dataset contains employee-level HR information such as department, employment status, gender, and marital status.

---

## 🔍 Step 1: Identify Duplicate Department Mappings

We begin by checking whether each `DeptID` correctly maps to a single `Department`.

SELECT DISTINCT DeptID, Department FROM HRDataset;

📌 Observation:
Some DeptID values are associated with multiple department names, indicating incorrect mappings.

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/e0299d09-6152-4358-ba2a-0bfb2764755b)

🛠 Step 2: Correct Department Mapping Errors
Issue Found in Admin Offices

SELECT Id, Employee_Name, DeptID, Department FROM HRDataset WHERE DeptID = 1 ORDER BY Department ASC;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/638a3490-e9ba-4eef-98b6-139e52c10f93)

🔎 Finding:
Employee Quinn, Sean was incorrectly assigned to Admin Offices instead of Software Engineering.

✅ Correction Applied

UPDATE HRDataset SET DeptID = 4 WHERE Id = 228;

📌 Result: Quinn, Sean is now correctly mapped.

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/b4b82a0d-c33a-479f-b74a-a0d1c40acc3d)

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/227c6fcd-932d-4bca-867b-966e7c39397d)

Issue Found in Sales Department

SELECT Id, Employee_Name, DeptID, Department FROM HRDataset WHERE DeptID = 6 ORDER BY Department ASC;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/8f28a49b-0935-4fa6-bd80-f06cc1227953)

🔎 Finding:
Employee Dee, Randy belonged to Production, not Sales.

UPDATE HRDataset SET DeptID = 5 WHERE Id = 65;

You will see that Dee, Randy has been moved to the Department Production from the Department Sales.

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/1f7c10af-270c-43a7-b29a-7e3d6071eef8)

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/8d51518a-a1c2-4b7e-927f-2ed2bc08bc01)

There is no longer a DeptID or Department mistake.

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/a3883d4e-f0e9-4791-baa9-e83c3f3fa8b1)

Find Unique Value for EmpStatusID and EmploymentStatus. Syntax as below:

SELECT DISTINCT EmpStatusID, EmploymentStatus FROM HRDataset;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/143d7dfc-d646-4306-ba81-a293daf3bdbb)

Once again we found that there is duplicate EmploymentStatus records.

Let's work on fixing EmpStatusID so that it is distinct for EmploymentStatus 'Terminated for Cause'. 16 records found EmploymentStatus as 'Terminated for Cause'.

SELECT Id, Employee_Name, EmpStatusID, EmploymentStatus FROM HRDataset WHERE EmploymentStatus = 'Terminated for Cause';

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/cec04fe7-8eb5-4203-8065-7d578cab3b75)

UPDATE HRDataset SET EmpStatusID = 
CASE ID
WHEN 96 THEN 4
WHEN 133 THEN 4
ELSE NULL
END
WHERE ID IN (96, 133);

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/b53da1d7-2a1f-4127-9f6a-96ce9a3add49)

Now will work on fixing EmpStatusID so that it is distinct for EmploymentStatus 'Active'. 207 records found EmploymentStatus as 'Active'.

SELECT Id, Employee_Name, EmpStatusID, EmploymentStatus FROM HRDataset WHERE EmploymentStatus = 'Active';

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/83074ca6-2646-4e6f-819d-bc1501ec376c)

UPDATE HRDataset SET EmpStatusID = 1 WHERE ID IN (40, 17, 52, 59, 135, 136, 178, 185, 247, 263, 295, 9, 20, 32, 62, 115, 117, 118, 145, 157, 170, 174, 193, 201, 252);

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/2e6d84f1-4a2c-4e59-bb3d-fdbb616bc61c)

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/344d08e4-a9d9-4dc6-ba21-d374191b5e23)

There is no longer a EmpStatusID or EmploymentStatus mistake.

To ensure the accuracy of the data, we must verify the following:

1. Check for duplicate EmployeeID entries.
2. Confirm if Employee Name, GenderID, and Gender match.
3. Validate whether Employee Name, MarritalStatusID, and MarritalDescription match.
4. Verify that each employee's department name corresponds to their Department ID.

To Check for duplicate EmployeeID entries.

SELECT EmpID FROM HRDataset GROUP BY EmpID HAVING COUNT(*) > 1;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/489d49d5-410a-41a3-b3c8-355462bab448)

Confirm if Employee Name, GenderID, and Gender match.

SELECT Employee_Name, GenderID, Sex FROM HRDataSet WHERE (Sex = 'Male' AND GenderID != 1) OR (Sex = 'Female' AND GenderID != 0);

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/7d2d9ae0-f736-4b5a-83e1-237f90106eda)

Validate whether Employee Name, MarritalStatusID, and MarritalDescription match.

SELECT Employee_Name, MaritalStatusID, MaritalDesc FROM HRDataSet WHERE (MaritalStatusID = 1 AND MaritalDesc != 'Married') OR (MaritalStatusID = 0 AND MaritalDesc != 'Single') OR (MaritalStatusID = 2 AND MaritalDesc != 'Divorced') OR (MaritalStatusID = 3 AND MaritalDesc != 'Separated') OR (MaritalStatusID = 4 AND MaritalDesc != 'Widowed');

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/ff161b4e-1567-4b48-a1d5-ac2f3c4b4177)

Verify that each employee's department name corresponds to their Department ID.

SELECT e.Employee_Name, e.Department AS EmployeeDeptName, e.DeptID AS EmployeeDeptID, d.Department AS CorrectDeptName, d.DeptID AS CorrectDeptID FROM HRDataSet e
JOIN HRDataSet d ON e.Employee_Name = d.Employee_Name WHERE e.Department != d.Department OR e.DeptID != d.DeptID;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/f99885ff-ca70-47cd-b756-c89149cdf46d)
