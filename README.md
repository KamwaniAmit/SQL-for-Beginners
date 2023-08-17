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
