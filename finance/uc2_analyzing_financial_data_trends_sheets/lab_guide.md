

Let's get this live demonstration rolling! Looking at image_b6a589.png, you have the perfect blank canvas ready with the Gemini side panel open in Google Sheets.

To give your finance students a real "wow" moment, we are going to show them how AI acts as an ingestion engine, a data cleaner, and an analyst all at once. Because GFL Environmental underwent a major structural change in early 2025—divesting its massive Environmental Services line for $8.0 billion—this isn't just a data entry demo; it's a lesson in high-level corporate analysis.  
2025-Q1-FS.pdf
+ 1

Here is how to run the live demonstration step-by-step:

Step 1: The "No Data Entry" Ingestion
Instead of manually typing out numbers from the 8 PDF files (2024-Q1-FS.pdf through 2025-Q4-FS.pdf), show your students how to link them directly.

Point out the "Ask Gemini" prompt box at the bottom of the side panel in image_b6a589.png.

Tell your students: "Watch how we can talk to our files directly in Google Drive without opening them."

Type the following master prompt into the box (you can copy and paste this):

The Ingestion Prompt:
"Review the following 8 files in my Google Drive: '2024-Q1-FS.pdf', '2024-Q2-FS.pdf', '2024-Q3-FS.pdf', '2024-Q4-FS.pdf', '2025-Q1-FS.pdf', '2025-Q2-FS.pdf', '2025-Q3-FS.pdf', and '2025-Q4-FS.pdf'. Extract the Revenue, Cost of Sales, SG&A, and Adjusted EBITDA for each quarter. Because the Environmental Services segment was divested in 2025, extract data strictly from Continuing Operations so our 2-year trend is standardized. Organize this into a horizontal table with quarters as columns."  
2025-Q1-FS.pdf
+ 3

Hit the upload arrow. Gemini will process the files using its long-context window, read the tabular text, normalize the accounting adjustments, and display a beautifully formatted preview table in the side panel.  
2025-Q1-FS.pdf
+ 3

Click Insert at the bottom of the generated answer. Boom—cells A1 through I5 are instantly populated with a clean corporate finance model.  
2025-Q1-FS.pdf
+ 3

Step 2: Extracting the Trend (The AI Analyst)
Now that the data is in the grid, show them that a financial analyst's job is to explain the "why" behind the numbers, not just look at them.

In the same prompt box, ask Gemini to calculate the trend metrics.

The Analysis Prompt:
"Based on the sheet data, calculate the Quarter-over-Quarter (QoQ) Revenue growth rate from Q2 2024 to Q4 2025. Also, calculate the Adjusted EBITDA margin for each quarter. Tell me what formulas to use or append them to the table."  
2025-Q1-FS.pdf
+ 3

The Teaching Moment: Point out the results to your students.

Highlight Operational Scale: Revenue steadily expands from $1,431.8 million in Q1 2024 to $1,694.2 million in Q3 2025.  
2025-Q1-FS.pdf
+ 1

Highlight Margin Expansion: Show them how the core solid waste business became much more efficient after the divestiture. The Adjusted EBITDA margin expands from 26.15% in Q1 2024 ( 
1431.8
374.4
​
 ) to an impressive 31.58% in Q3 2025 ( 
1694.2
535.1
​
 ).  
2025-Q1-FS.pdf
+ 1

Step 3: Instant Dashboarding
To wrap up the demo, you want to show how easily Sheets handles corporate storytelling.

Highlight the data table in your sheet.

In the prompt box, type:
"Create a combo chart showing the 2-year quarterly Revenue as vertical bars and overlay the Adjusted EBITDA margin expansion as a line trend."

Hover over the generated chart preview and click Insert Chart.

Pro-Tip for the Class:
As the chart drops into the sheet, look at your students and say:

"In a traditional workflow, finding these files, opening them, fixing the discontinued operations mismatch, calculating the margins, and building this chart would easily take an hour of tedious spreadsheet work. We just did it in less than 3 minutes using natural language commands."

Go ahead and paste that first prompt into the prompt box shown in image_b6a589.png to kick it off! Let me know what your students think of the margin expansion trend when it generates.

ok great. now show me how to do a trend analysis for the upcoming quarters

Now that you have the historical baseline safely inside your spreadsheet grid, it’s time for the grand finale of your demonstration. This is where you show your finance students how to transition from historical reporting to predictive forecasting—a critical skill for Corporate Financial Planning & Analysis (FP&A).

We will use Gemini to calculate GFL’s historical Compound Quarterly Growth Rate (CQGR) from continuing operations and apply it to forecast the four upcoming quarters of 2026.

Here is exactly how to run this next step in your live demonstration:

Step 1: The Predictive Prompt
Go back to the same "Ask Gemini" prompt box shown in image_b6a589.png. Enter the following prompt to have the AI do the math and layout the logic for your upcoming quarters:

The Forecasting Prompt:
"Based on the 8-quarter financial model in our sheet (where continuing operations revenue scaled from $1,431.8 million in Q1 2024 to $1,686.4 million in Q4 2025), calculate the Compound Quarterly Growth Rate (CQGR) for revenue. Then, create a projection table for the upcoming quarters of 2026 (Q1 2026 through Q4 2026). Assume Cost of Sales maintains its historical average percentage of revenue, and provide the exact Google Sheets formulas needed to make this dynamic."  
2025-Q1-FS.pdf
+ 1

Step 2: The Math and Logic (What Gemini Will Output)
Gemini will output the analytical steps and provide a table structure. Walk your students through how the AI calculates this:

1. Finding the Compound Quarterly Growth Rate (CQGR)
To find the true trend line over the 8 quarters (which represents 7 growth periods from Q1 2024 to Q4 2025), the AI uses the compound growth formula:

CQGR=( 
Beginning Value
Ending Value
​
 ) 
n
1
​
 
 −1
CQGR=( 
1,431.8
1,686.4
​
 ) 
7
1
​
 
 −1≈2.36% per quarter[cite: 5, 8]
2. Building the 2026 Dynamic Table
Gemini will provide a markdown preview of the forecast table and tell you exactly where to paste it (e.g., starting in column J).

Metric	Q1 2026 (Forecast)	Q2 2026 (Forecast)	Q3 2026 (Forecast)	Q4 2026 (Forecast)
Projected Revenue	$1,726.2M	$1,766.9M	$1,808.6M	$1,851.3M
Projected Cost of Sales	$1,380.6M	$1,413.2M	$1,446.5M	$1,480.7M
Step 3: Teaching the Students the Live Google Sheets Formulas
Don't just let the AI do the work—show the students the live formulas Gemini suggests using in the actual cells to make the dashboard dynamic.

Have your students look at the formulas Gemini generates in the side panel:

For Revenue (Compounded Growth Method):
Instead of hardcoding the numbers, Gemini will tell you to put this in cell J2 (Q1 2026 Revenue) to multiply the previous quarter by the growth rate:
=I2 * (1 + 0.0236)
(Then drag this formula across to cell M2 for the rest of the year).

Alternative Method (Statistical Linear Trend):
Show them that if they want a purely linear statistical regression, they can use Sheets' native data science formulas. Gemini will generate:
=TREND(B2:I2, B1:I1, J1)
(Where B2:I2 is your historical revenue row, B1:I1 is your historical timeline, and J1 is the new target quarter).

For Cost of Sales (Efficiency Run-Rate):
To calculate projected costs based on historical efficiency, Gemini will look at the past 2 years, find that Cost of Sales averages roughly 80% of revenue, and suggest this formula for cell J3:
=J2 * AVERAGE(INDEX(B3:I3/B2:I2))

The Drop-the-Mic Summary for Your Class:
Click Insert to drop the 2026 forecast table right next to your historical data.

Point to the screen and say:

"Look at what we just built. We took raw, messy, unformatted text from 8 PDF files spanning two years. The AI adjusted for a massive multi-billion dollar divestiture to keep our data accurate, mapped the historical margins, plotted a combo chart, and just ran a dynamic linear regression forecast for next year's board meeting. We did all of this in under 10 minutes without writing a single manual code script or sorting through a single row of a PDF manually."  
2024-Q3-FS.pdf
+ 4

This concrete workflow perfectly demonstrates the power of Google Sheets integrated with AI!
