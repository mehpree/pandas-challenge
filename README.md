# PyCitySchools Data Analysis

Welcome to the PyCitySchools data analysis project! Assuming I am the Chief Data Scientist for a city's school district, I've conducted a comprehensive analysis of standardized test results and school-related data. This analysis aims to assist the school board and the mayor in making informed decisions regarding future school budgets and priorities. Below, I'll provide an overview of the key findings and trends discovered during this analysis.

### District Summary
In the district summary, I've calculated essential metrics that provide a high-level snapshot of our school district's performance:

- Total number of unique schools
- Total number of students
- Total budget
- Average math score
- Average reading score
- Percentage of students passing math
- Percentage of students passing reading
- Overall passing rate (percentage of students passing both math and reading)

### School Summary
The school summary delves into more detailed metrics for each school in our district:

- School name
- School type
- Total number of students
- Total school budget
- Per student budget
- Average math score
- Average reading score
- Percentage of students passing math
- Percentage of students passing reading
- Overall passing rate (percentage of students passing both math and reading)
  
### Top-Performing Schools
  I've identified the top-performing schools based on the percentage of students passing both math and reading. The top five schools are listed in descending order of overall passing percentage in the "top_schools" DataFrame.

### Lowest-Performing Schools
Similarly, I've identified the lowest-performing schools based on the percentage of students passing both math and reading. The bottom five schools are listed in ascending order of overall passing percentage in the "bottom_schools" DataFrame.

### Math Scores by Grade
The analysis includes a breakdown of average math scores for students of each grade level (9th, 10th, 11th, 12th) at each school.

### Reading Scores by Grade
A similar breakdown is provided for average reading scores for students of each grade level (9th, 10th, 11th, 12th) at each school.

### Scores by School Spending
I've categorized school performance based on average spending ranges per student. Four spending ranges were defined, and the analysis calculated various metrics for each range, including average math and reading scores, and the percentage of students passing math, reading, and both subjects.

Used the code provided below to create four bins with reasonable cutoff values to group school spending.
```python
spending_bins = [0, 585, 630, 645, 680]
labels = ["<$585", "$585-630", "$630-645", "$645-680"]

```

Used  `pd.cut`  to categorize spending based on the bins & the following code to then calculate mean scores per spending range.

```python
spending_math_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"])["Average Math Score"].mean()
spending_reading_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"])["Average Reading Score"].mean()
spending_passing_math = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Passing Math"].mean()
spending_passing_reading = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Passing Reading"].mean()
overall_passing_spending = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Overall Passing"].mean()
```

### Scores by School Size
The analysis also categorized school performance based on school size. Three size categories (small, medium, large) were defined, and the analysis calculated key metrics for each category, similar to the spending analysis.

Used the following code to bin the  `per_school_summary`.

```python
size_bins = [0, 1000, 2000, 5000]
labels = ["Small (<1000)", "Medium (1000-2000)", "Large (2000-5000)"]

```

Used  `pd.cut`  on the "Total Students" column of the  `per_school_summary`  DataFrame.

### Scores by School Type
Finally, the analysis looked at school performance based on school type (charter or district). The "type_summary" DataFrame provides insights into school performance, including average math and reading scores, and the percentage of students passing math, reading, and both subjects.

Used the `per_school_summary` DataFrame from the previous step to create a new DataFrame called `type_summary`.

### Observable Trends
Based on this comprehensive analysis, I've identified two notable trends:

- Charter Schools Outperform District Schools: Charter schools consistently outperform district schools in terms of overall passing rates. This suggests that charter school models may be worth exploring further for improving education in our city.

- Small and Medium-Sized Schools Excel: Smaller and medium-sized schools tend to have higher overall passing rates compared to larger schools. This implies that smaller class sizes and more personalized education may contribute to better student outcomes.

These trends provide valuable insights for decision-makers as they consider budget allocation and school priorities in our city's education system.

You can find the complete analysis and code in the provided Jupyter notebook, "PyCitySchools.ipynb". Feel free to explore the data and analysis further.

### References
Data generated by [Mockaroo, LLCLinks to an external site.](https://mockaroo.com/), (2022). Realistic Data Generator. Data for this dataset was generated by edX Boot Camps LLC, and is intended for educational purposes only.
