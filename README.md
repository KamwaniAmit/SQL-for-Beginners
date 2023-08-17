# SQL-for-Beginners
Learning Microsoft Transact SQL

Find Unique Value for DeptID and Department. Syntax as below:

SELECT DISTINCT DeptID, Department FROM HRDataset;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/e0299d09-6152-4358-ba2a-0bfb2764755b)

You will find that DeptID duplicates. We must correct the records before proceeding further.

Let's first see Admin Offices. Syntax as below:

SELECT Id, Employee_Name, DeptID, Department FROM HRDataset WHERE DeptID = 1 ORDER BY Department ASC;

![image](https://github.com/KamwaniAmit/SQL-for-Beginners/assets/142380910/638a3490-e9ba-4eef-98b6-139e52c10f93)
