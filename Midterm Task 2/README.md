# Midterm Lab Task 2: Data Cleaning and Transformation Using Power Query Editor
## Task Description: 
- To extract useful information from the file UncleanedDSJObs.csv (See raw file) taken from a Job Posting site available in Kaggle.
- To find out:
- -Which Job Roles pay the highest and least
- -What size companies pay the best
- -Where Job Roles or Job Titles pay the best and least in a specific state
## Dataset Before Cleaning and Transformation:


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

## Advanced Editor Code:
let
    Source = Excel.Workbook(File.Contents("C:\Users\Computer LAB\Downloads\Uncleaned_DS_jobs.xlsx"), null, true),
    Uncleaned_DS_jobs_Sheet = Source{[Item="Uncleaned_DS_jobs",Kind="Sheet"]}[Data],
    #"Promoted Headers" = Table.PromoteHeaders(Uncleaned_DS_jobs_Sheet, [PromoteAllScalars=true]),
    #"Changed Type" = Table.TransformColumnTypes(#"Promoted Headers",{{"index", Int64.Type}, {"Job Title", type text}, {"Salary Estimate", type text}, {"Job Description", type text}, {"Rating", type number}, {"Company Name", type text}, {"Location", type text}, {"Headquarters", type any}, {"Size", type any}, {"Founded", Int64.Type}, {"Type of ownership", type any}, {"Industry", type any}, {"Sector", type any}, {"Revenue", type any}, {"Competitors", type any}}),
    #"Extracted Text Before Delimiter" = Table.TransformColumns(#"Changed Type", {{"Salary Estimate", each Text.BeforeDelimiter(_, "("), type text}}),
    #"Inserted Text Between Delimiters" = Table.AddColumn(#"Extracted Text Before Delimiter", "Text Between Delimiters", each Text.BetweenDelimiters([Salary Estimate], "$", "K"), type text),
    #"Renamed Columns" = Table.RenameColumns(#"Inserted Text Between Delimiters",{{"Text Between Delimiters", "Min sal."}}),
    #"Inserted Text Between Delimiters1" = Table.AddColumn(#"Renamed Columns", "Text Between Delimiters", each Text.BetweenDelimiters([Salary Estimate], "$", "K", 1, 0), type text),
    #"Renamed Columns1" = Table.RenameColumns(#"Inserted Text Between Delimiters1",{{"Text Between Delimiters", "Max sal."}}),
    #"Added Custom" = Table.AddColumn(#"Renamed Columns1", "Role Type", each if Text.Contains([Job Title], "Data Scientist") then
"Data Scientist"
else if Text.Contains([Job Title], "Data Analyst") then
"Data Analyst"
else if Text.Contains([Job Title], "Data Engineer") then
"Data Engineer"

else if Text.Contains([Job Title], "Machine Learning") then
"Machine Learning Engineer"
else
"other"),
    #"Added Custom1" = Table.AddColumn(#"Added Custom", "State Abbreviations", each if [Location]= "New Jersey" then ", NJ"
else if [Location] = "Remote" then ", other"
else if [Location]= "United States" then ", other"
else if [Location]= "Texas" then ", TX"
else if [Location]= "Patuxent" then ", MA"
else if [Location]= "California" then ", CA"
else if [Location]= "Utah" then ", UT"
else [Location]),
    #"Split Column by Delimiter" = Table.SplitColumn(#"Added Custom1", "State Abbreviations", Splitter.SplitTextByDelimiter(",", QuoteStyle.Csv), {"State Abbreviations.1", "State Abbreviations.2"}),
    #"Changed Type1" = Table.TransformColumnTypes(#"Split Column by Delimiter",{{"State Abbreviations.1", type text}, {"State Abbreviations.2", type text}}),
    #"Replaced Value" = Table.ReplaceValue(#"Changed Type1","Anne Rundell","MA",Replacer.ReplaceText,{"State Abbreviations.2"}),
    #"Inserted Text Before Delimiter" = Table.AddColumn(#"Replaced Value", "Text Before Delimiter", each Text.BeforeDelimiter([Size], " "), type text),
    #"Renamed Columns2" = Table.RenameColumns(#"Inserted Text Before Delimiter",{{"Text Before Delimiter", "Min. Company Size"}}),
    #"Inserted Text Between Delimiters2" = Table.AddColumn(#"Renamed Columns2", "Max Company Size", each Text.BetweenDelimiters([Size], " ", " ", 1, 0), type text),
    #"Inserted Text Before Delimiter1" = Table.AddColumn(#"Inserted Text Between Delimiters2", "Text Before Delimiter", each Text.BeforeDelimiter([Company Name], "#(lf)"), type text),
    #"Removed Columns" = Table.RemoveColumns(#"Inserted Text Before Delimiter1",{"Company Name"}),
    #"Renamed Columns3" = Table.RenameColumns(#"Removed Columns",{{"Text Before Delimiter", "Company Name"}}),
    #"Removed Columns1" = Table.RemoveColumns(#"Renamed Columns3",{"Job Description"})
in
    #"Removed Columns1"


## Final Output
### Cleaned Data
![image](https://github.com/user-attachments/assets/077daa3f-2cb6-4226-8c45-c751f709383b)


### Sal By Role Type Dup
![image](https://github.com/user-attachments/assets/b34c7f35-c2b3-49ec-a0a2-2da404883eb3)


### Sal By Role Size Ref
![image](https://github.com/user-attachments/assets/2cda21a0-228d-4a2b-99e9-2adf2ee59bf3)


### Sal By State Ref
![image](https://github.com/user-attachments/assets/b1636d15-e9e3-4f9c-9909-11bb1c7cc26e)



### Query Dependencies
![image](https://github.com/user-attachments/assets/a6d095c6-f479-4f1a-8919-5c37fd631c2c)
