# SQL-for-Beginners
Learning Microsoft Transact SQL

Find Unique Value for DeptID and Department. Syntax as below:

SELECT DISTINCT DeptID, Department FROM HRDataset;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/e0299d09-6152-4358-ba2a-0bfb2764755b)

You will find that DeptID duplicates. We must correct the records before proceeding further.

Let's first go to Admin Offices and find what's wrong? Syntax as below:

SELECT Id, Employee_Name, DeptID, Department FROM HRDataset WHERE DeptID = 1 ORDER BY Department ASC;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/638a3490-e9ba-4eef-98b6-139e52c10f93)

We found that Quinn, Sean belongs to the Software Engineering Department, although the DeptID must be 4 rather than 1. To correct the records below is syntax:

UPDATE HRDataset SET DeptID = 4 WHERE Id = 228;

You will see that Quinn, Sean has been moved to the Department Software Engineering from the Department Admin Offices.

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/b4b82a0d-c33a-479f-b74a-a0d1c40acc3d)

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/227c6fcd-932d-4bca-867b-966e7c39397d)

Let's checkout the Sales Department. Syntax as below:

SELECT Id, Employee_Name, DeptID, Department FROM HRDataset WHERE DeptID = 6 ORDER BY Department ASC;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/8f28a49b-0935-4fa6-bd80-f06cc1227953)

Let's correct the error by amending DeptID for Dee, Randy and syntax is as followed:

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
