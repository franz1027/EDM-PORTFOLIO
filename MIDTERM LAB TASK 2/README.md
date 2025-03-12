## Midterm Lab Task 2 – Data Cleaning and Transformation 
## Using Power Query Editor

Company X would like to extract some useful information from the UnclenedDSJObs csv taken
from a Job Posting site available in Kaggle. 

There are a lot of columns available but focus only
on generating insights that will answer the ff: questions

1. exWhich Job Roles pay the highest and least
2. What size companies pay the best
3. Where Job Roles or Job Titles pay the best and least in a specific state

   ## data-cleaning task
- Salary Estimate Column – Remove All the characters after the ( open
parentheses)
 - Create 2 New Columns (From the Salary Estimate) Min Sal and Max Sal
 - ADD COLUMN – Role Type
 - SPLIT COLUMNS by Delimeter
 - Select Location column (SPLIT columns by , Delimeter)
## Reshape and Group the tables:
- Create a duplicate of the raw data Right Click Unclean DS Jobs select
duplicate (Queries pane)
- Rename the duplicate with “Sal By Role Type dup”
- Create a reference of the raw data Right Click Unclean DS Jobs
choose reference (Queries pane)
- Rename the reference with “Sal By Role Size ref
- Mapping Other Files and include in the current queries
- Create a reference of the raw data Right Click Unclean DS Jobs
- choose reference (Queries pane)
- Rename the reference with “Sal By State ref
- To view dependencies and References of the QUERIES
## clean data
![Sample Output](image/uncleaned.png)
## sal by type
![Sample Output ](image/sal%20by%20role%20type%20dup.png).
## sal ref
![Sample Output ](image/sal%20ref.png).
## sal size
![Sample Output](image/sal%20size.png)
## uncleaned
![Sample Output ](IMAGE/clean%20data.png).
## table
![Sample Output ](image/table.png).

