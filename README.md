# pandas-challenge
Module 4 assignment for U of T BootCamp

1. Data Loading and Merging
The data was first manually copy pasted into one file and then loaded from two sheets:
•	students_complete: Contains individual student performance data.
•	schools_complete: Contains school-level information such as budget and school type.
I merged these datasets to have all the relevant information in one DataFrame for easy analysis. The merge was based on the school_name column, which appears in both sheets.
2. District Summary Calculations
I performed the following calculations to create an overview of the district's performance:
•	Total Schools: The count of unique schools in the dataset.
•	Total Students: The total number of students in the district.
•	Total Budget: The sum of all school budgets.
•	Average Math and Reading Scores: The mean of math and reading scores across all students.
•	% Passing Math and Reading: The percentage of students scoring 70 or above in math and reading.
•	% Overall Passing: The percentage of students who passed both math and reading (i.e., scored 70 or above in both).
3. School-Level Summary
I calculated key performance metrics for each school:
•	Total Students: The number of students at each school.
•	Total School Budget: The total budget for each school.
•	Per Student Budget: The total budget divided by the number of students.
•	Average Math and Reading Scores: The mean scores for each school.
•	% Passing Math, Reading, and Overall: The percentage of students passing math, reading, and both at each school.

4. Top and Bottom Schools
I sorted the schools based on the % Overall Passing metric to identify the top 5 and bottom 5 performing schools.
5. Scores by Grade
I created separate DataFrames to calculate the average math and reading scores for each grade (9th, 10th, 11th, and 12th) at each school using a pivot table.
6. School Performance by Spending
I used predefined bins to group schools by their per-student budget:
spending_bins = [0, 585, 630, 645, 680]
labels = ["<$585", "$585-630", "$630-645", "$645-680"]
I then calculated the average math and reading scores, as well as the percentage of students passing math, reading, and both subjects for each spending range.
7. Performance by School Size
I categorized schools into three size ranges based on the number of students:
•	Small (<1000 students)
•	Medium (1000-2000 students)
•	Large (2000-5000 students)
I calculated the same performance metrics (average scores and passing percentages) for each size category.
8. Performance by School Type
I grouped schools by type (Charter or District) and calculated the average scores and passing percentages for each type.





Calculations
1.	Overall Passing Calculation: To determine the percentage of students passing both math and reading, I used a combination of boolean logic to check if students passed both subjects:
% Overall Passing = ((math_score >= 70) & (reading_score >= 70)).mean() * 100
This checks if both conditions are met and then calculates the percentage of students satisfying both.
2.	Spending and Size Binning: To group schools based on spending or size, I used the pd.cut() function, which allows us to categorize continuous variables into discrete bins:
school_summary_df["Spending Ranges (Per Student)"] = pd.cut(school_summary_df["Per Student Budget"], bins=spending_bins, labels=labels)

This enables us to analyze performance trends within distinct ranges of spending or size.
Summary of Outputs
•	District Summary: A high-level overview of district performance.
•	School Summary: Key performance metrics for each individual school.
•	Top/Bottom Schools: Lists of the top 5 and bottom 5 performing schools by overall passing percentage.
•	Scores by Grade: Average math and reading scores for each grade level (9th, 10th, 11th, and 12th).
•	Spending Summary: School performance broken down by per-student spending ranges.
•	Size Summary: School performance based on school size.
•	Type Summary: School performance based on school type (Charter or District).

