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

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/44dfade0-c439-460c-9823-451227bcd21f)

Once again we found that there is duplicate EmploymentStatus records.

Let's work on fixing EmpStatusID so that it is distinct for EmploymentStatus 'Active'. 207 records found EmploymentStatus as 'Active'.

SELECT Id, Employee_Name, EmpStatusID, EmploymentStatus FROM HRDataset WHERE EmploymentStatus = 'Active';

