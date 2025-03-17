# Midterm Lab Task 2: Data Cleaning and Transformation Using Power Query Editor
## Task Description: 
- To extract useful information from the file UncleanedDSJObs.csv (See raw file) taken from a Job Posting site available in Kaggle.
- To find out:
- -Which Job Roles pay the highest and least
- -What size companies pay the best
- -Where Job Roles or Job Titles pay the best and least in a specific state
## Dataset Before Cleaning and Transformation:
![image](https://github.com/user-attachments/assets/db880878-c005-43a1-9487-f59aade2cf97)


## Steps Performed in Data Cleaning and Transformation:
- Duplicated the raw data to preserve the original.
- Cleaned the salary estimate column by removing everything after the "(" symbol.
- Created Min Sal and Max Sal columns from the salary estimate.
- Added a new column Role Type to classify jobs as "data scientist", "data analyst", "data engineer", "machine learning engineer", or "other" based on the job title.
- Corrected the location column with custom states and split it into city and state abbreviation.
- Replaced incorrect state entries (e.g., "anne rundell" to "ma").
- Split the company size column to extract MinCompanySize and MaxCompanySize, and removed the word "employees".
- Replaced invalid or negative values:
- Competitors: replaced -1 with "n/a".
- Revenue: replaced negatives with 0.
- Industry: replaced -1 with "other".
- Cleaned company name by removing extra ratings or numbers at the end.
- Removed unnecessary columns like job descriptions.
- Duplicated the cleaned data as Sal By Role Type dup, selected Role Type, Min Sal, and Max Sal, converted salaries to currency, multiplied by 1000, and grouped by - Role Type to get average salaries.
- Created a reference as Sal By Role Size ref, selected Size, Min Sal, and Max Sal, multiplied salaries by 1000, and grouped by Size to get average salaries.
- Imported a State Mapping file to map state abbreviations to full state names and merged it with the dataset.
- Created a reference as Sal By State ref, selected State Full Name, Min Sal, and Max Sal, multiplied salaries by 1000, and grouped by State Full Name to get average salaries.
- Checked query dependencies to confirm correct relationships.

## Final Output
### Cleaned Data
![image](https://github.com/user-attachments/assets/eaebb2d5-66df-4af3-b137-ec5b55cfd51b)


### Sal By Role Type Dup
![image](https://github.com/user-attachments/assets/6f122ef8-f7f7-41d2-969f-b9ba4271c4c2)


### Sal By Role Size Ref
![image](https://github.com/user-attachments/assets/d3f65639-01f3-4c53-82d1-8da052d53569)

### Sal By State Ref
![image](https://github.com/user-attachments/assets/91ac5387-8594-4caa-944b-8595b9c14466)



### Query Dependencies
![image](https://github.com/user-attachments/assets/6cf122f7-011d-4f41-841e-4041f988518a)
