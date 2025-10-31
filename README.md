This data was originally calculated using the USBR 24-Month Study Projections found at 24-Month Study Projections, and this data is specifically using the Probable Minimum 24-Month Study released on August 15 2025, found here https://www.usbr.gov/lc/region/g4000/24mo_MIN.pdf . 
If you would like to use the newest data from the USBR here is instructions on how to reproduce my results:

1.	Extract the Lake Powell data from the USBR PDF:
  a.	Open the latest 24-Month Study PDF.
  b.	Copy the Lake Powell page and paste it into a .txt file.
2.	Format the .txt file for Excel import:
  a.	Remove extra spaces within column titles.
  b.	Ensure each title is clearly separated by a single space.
  c.	Make sure to remove the space between the month and the year in the columns
3.	Save this .txt file
4.	Open the Excel workbook USBR24moLakeMead.xlsx from this repository.
  a.	Select the sheet where you want to import the data.
  b.	You can rename the sheet or the excel file but be sure to update the names in the Python code.
5.	In Excel, go to:
  a.	Data → Get Data → From File → From Text/CSV
  b.	Select and open your .txt file.
6.	Click Transform Data to open the Power Query editor.
7.	In Power Query:
  a.	Choose Split Column → By Delimiter
  b.	Select Space (or the delimiter you used when formatting).
8.	Click Close & Load to import the data.
9.	Check data alignment
  a.	Make sure the date appears in a single column.
    i.	If column headers don’t match the number of data columns, a space was likely missed.
    ii.	Common mistake: leaving a space between month and year (e.g., “Sep 2024” becomes two columns).
  b.	I personally find it easier to fix the .txt file and reimport (steps 4–8), but you can also adjust formatting directly in Excel.
10.	Add two new columns at the end of the data.
11.	In the first new column:
  a.	Enter =B3/1000 and drag down.
  b.	This converts Lake Powell Unregulated Inflow from thousand acre-feet to million acre-feet (typically column 1.2).
12.	 Delete values in the WY (Water Year) row.
13.	 In the second new column:
  a.	Use =SUM(...) to total inflow over 12 months.
  b.	Be careful: the WY row may interrupt the sequence.
  c.	For example, if the WY row appears after the first September, sum from Sep 2024 to Aug 2025.
14.	 Repeat for the next 12-month block.
15.	You should now have three annual inflow values.
16.	Insert these into the appropriate rows in the Inflow Graph sheet.
  a.	This sheet provides a preview of the figure.
  b.	Note: some lines are edited out in the Python graph.
  c.	Immersive Model Scenario 1 and 2 are based on the two lowest 3-year averages from the 3yearsMinimumHydrologyResults.xlsx file, which are already included in the Inflow Graph sheet.
17.	Save the Excel file.
18.	Run the Python code.
a.	You can modify the code to include more or fewer lines from the Inflow Graph sheet.

