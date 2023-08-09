
# TASK 1

// Select the department name and calculate the average monthly salary

SELECT dpt.DEPARTMENT_NAME, AVG(sal.AMOUNT) AS AVERAGE_MONTHLY_SALARY_USD
FROM Salaries sal

JOIN Employees emp ON emp.id = sal.EMPLOYEE_ID

JOIN Departments dpt ON dpt.ID = emp.DEPARTMENT_ID

GROUP BY dpt.DEPARTMENT_NAME  //Group the results by department name

ORDER BY AVERAGE_MONTHLY_SALARY_USD DESC // Sort the average salary in descending order

LIMIT 3; -- Limit the output to the top 3 departments



# Task 2

import pandas as pd

// Load the CSV files into DataFrames

departments = pd.read_csv("C:\\Users\\mail2\\OneDrive\\Desktop\\Assignment\\ASDE-Departments.csv")

employees = pd.read_csv("C:\\Users\\mail2\\OneDrive\\Desktop\\Assignment\\ASDE-Employees.csv")

salaries = pd.read_csv("C:\\Users\\mail2\\OneDrive\\Desktop\\Assignment\\ASDE-Salaries.csv")

//Merge the Data to create a combined dataset

merged_df = pd.merge(departments, employees, left_on='ID', right_on='DEPT_ID')
combined_data = pd.merge(merged_df, salaries, left_on='ID_y', right_on='EMP_ID')
-- Calculate the average monthly salary for each department
average_salary_per_department = combined_data.groupby(['NAME_x'])['AMT'].mean()

//Get the top 3 departments with the highest average salary
 
top_departments = average_salary_per_department.sort_values(ascending=False).head(3)

print(top_departments)


# Task 3


def compute(n):

if n < 10: 

out = n ** 2

elif n < 20: 

out = 1 for i in range(1, n-9): // change the value from (n-10)--> (n-9) 
out *= i 

else: lim = n - 19 // Change the value from (n-20) --> (n-19)

out = lim * lim out = out - lim

out = out / 2 print(out)

n = int(input("Enter an integer: ")) compute(n)

# Task 4

![Screenshot 2023-08-09 164007](https://github.com/Vishakha02D2/ASDE_Assignments/assets/120273836/d5491558-fd65-47f1-8d64-0baf39a28b07)

Step 1: Obtain the sample TSV file.

Step 2: Extract the first column's entries and line numbers associated with the 'Xerox' item using the command below. This will generate an output file named output.tsv:

-- awk -F'\t' '$1 ~ /^Xerox/ {print $1, FNR}' sample.tsv > output.tsv

Step 3:Sort the rows by item name with the following command

--sort -k1 output.tsv -o output.tsv

Step 4: Running the following command to process the output.tsv file. 

--cat output.tsv | tee >(wc -l) | tee >(sha1sum) | tail -5


# Task 5

For Linux 

cat /etc/group

For Windows (using Git Bash): 

ls -l | awk '{print $3}' | sort | uniq -d

