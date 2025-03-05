let
    Source = Excel.Workbook(File.Contents("D:\franz\uncleaned.xlsx"), null, true),
    Uncleaned_DS_jobs_Sheet = Source{[Item="Uncleaned_DS_jobs",Kind="Sheet"]}[Data],
    #"Promoted Headers" = Table.PromoteHeaders(Uncleaned_DS_jobs_Sheet, [PromoteAllScalars=true]),
    #"Changed Type" = Table.TransformColumnTypes(#"Promoted Headers",{{"index", Int64.Type}, {"Job Title", type text}, {"Salary Estimate", type text}, {"Job Description", type text}, {"Rating", type number}, {"Company Name", type text}, {"Location", type text}, {"Headquarters", type any}, {"Size", type any}, {"Founded", Int64.Type}, {"Type of ownership", type any}, {"Industry", type any}, {"Sector", type any}, {"Revenue", type any}, {"Competitors", type any}}),
    #"Extracted Text Before Delimiter" = Table.TransformColumns(#"Changed Type", {{"Salary Estimate", each Text.BeforeDelimiter(_, "("), type text}}),
    #"Sorted Rows" = Table.Sort(#"Extracted Text Before Delimiter",{{"Salary Estimate", Order.Ascending}}),
    #"Inserted Text Between Delimiters" = Table.AddColumn(#"Sorted Rows", "Min Value", each Text.BetweenDelimiters([Salary Estimate], "$", "K"), type text),
    #"Reordered Columns" = Table.ReorderColumns(#"Inserted Text Between Delimiters",{"index", "Job Title", "Min Value", "Salary Estimate", "Job Description", "Rating", "Company Name", "Location", "Headquarters", "Size", "Founded", "Type of ownership", "Industry", "Sector", "Revenue", "Competitors"}),
    #"Renamed Columns" = Table.RenameColumns(#"Reordered Columns",{{"Min Value", "Min Sal"}}),
    #"Inserted Text Between Delimiters1" = Table.AddColumn(#"Renamed Columns", "MAX SAL ", each Text.BetweenDelimiters([Salary Estimate], "$", "K"), type text),
    #"Reordered Columns1" = Table.ReorderColumns(#"Inserted Text Between Delimiters1",{"index", "Job Title", "Min Sal", "Salary Estimate", "MAX SAL ", "Job Description", "Rating", "Company Name", "Location", "Headquarters", "Size", "Founded", "Type of ownership", "Industry", "Sector", "Revenue", "Competitors"}),
    #"Added Custom" = Table.AddColumn(#"Reordered Columns1", "Role Type", each if Text.Contains([Job Title], "Data Scientist") then
"Data Scientist"
else if Text.Contains([Job Title], "Data Analyst") then
"Data Analyst"
else if Text.Contains([Job Title], "Data Engineer") then
"Data Engineer"
else if Text.Contains([Job Title], "Machine Learning") then
"Machine Learning Engineer"
else
"other"),
    #"Changed Type1" = Table.TransformColumnTypes(#"Added Custom",{{"Role Type", type text}}),
    #"Filtered Rows" = Table.SelectRows(#"Changed Type1", each true),
    #"Reordered Columns2" = Table.ReorderColumns(#"Filtered Rows",{"index", "Job Title", "Min Sal", "Salary Estimate", "MAX SAL ", "Role Type", "Job Description", "Rating", "Company Name", "Location", "Headquarters", "Size", "Founded", "Type of ownership", "Industry", "Sector", "Revenue", "Competitors"}),
    #"Added Custom1" = Table.AddColumn(#"Reordered Columns2", "Custom", each if [Location]= "New Jersey" then ", NJ"
else if [Location] = "Remote" then ", other"
else if [Location]= "United States" then ", other"
else if [Location]= "Texas" then ", TX"
else if [Location]= "Patuxent" then ", MA"
else if [Location]= "California" then ", CA"
else if [Location]= "Utah" then ", UT"
else [Location]),
    #"Split Column by Delimiter" = Table.SplitColumn(#"Added Custom1", "Custom", Splitter.SplitTextByDelimiter(",", QuoteStyle.Csv), {"Custom.1", "Custom.2"}),
    #"Changed Type2" = Table.TransformColumnTypes(#"Split Column by Delimiter",{{"Custom.1", type text}, {"Custom.2", type text}}),
    #"Removed Columns" = Table.RemoveColumns(#"Changed Type2",{"Custom.1", "Custom.2"}),
    #"Sorted Rows1" = Table.Sort(#"Removed Columns",{{"Location", Order.Ascending}}),
    #"Added Custom2" = Table.AddColumn(#"Sorted Rows1", "Custom", each if [Location]= "New Jersey" then ", NJ"
else if [Location] = "Remote" then ", other"
else if [Location]= "United States" then ", other"
else if [Location]= "Texas" then ", TX"
else if [Location]= "Patuxent" then ", MA"
else if [Location]= "California" then ", CA"
else if [Location]= "Utah" then ", UT"
else [Location]),
    #"Split Column by Delimiter1" = Table.SplitColumn(#"Added Custom2", "Custom", Splitter.SplitTextByDelimiter(",", QuoteStyle.Csv), {"Custom.1", "Custom.2"}),
    #"Changed Type3" = Table.TransformColumnTypes(#"Split Column by Delimiter1",{{"Custom.1", type text}, {"Custom.2", type text}}),
    #"Reordered Columns3" = Table.ReorderColumns(#"Changed Type3",{"index", "Job Title", "Min Sal", "Salary Estimate", "MAX SAL ", "Role Type", "Job Description", "Rating", "Company Name", "Location", "Custom.1", "Custom.2", "Headquarters", "Size", "Founded", "Type of ownership", "Industry", "Sector", "Revenue", "Competitors"}),
    #"Renamed Columns1" = Table.RenameColumns(#"Reordered Columns3",{{"Custom.1", "LOCATION NAME"}, {"Custom.2", "LOCATION ACRO"}})
in
    #"Renamed Columns1"
