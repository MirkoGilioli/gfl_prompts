# Leveraging Generative AI in Google Sheets: Corporate FP&A Case Study
## Student Lab Guide & Interactive Tutorial
**Focus Area:** Financial Data Ingestion, Normalization, Trend Analysis, and Predictive Forecasting (GFL Environmental Case Study)

---

## 1. Course Overview & Business Scenario

### The Financial Challenge: Divestitures and Discontinued Operations
In corporate finance, tracking performance across multiple quarters is rarely as simple as copying and pasting numbers from consecutive earnings reports. Mergers, acquisitions, and divestitures frequently disrupt historical consistency. 

This lab focuses on **GFL Environmental Inc.**, a major environmental services company. In early 2025, GFL underwent a monumental structural transformation: **it divested its massive Environmental Services line for $8.0 billion in cash**. 

As a financial analyst, this presents a major challenge:
* **The Problem:** The historical reports from 2024 include the divested segment's revenues and expenses. The 2025 reports separate these out as "discontinued operations." If you simply copy and paste the raw "Total Revenue" figures, your 2-year trend line will be highly distorted and financially meaningless.
* **The Analytical Goal:** You must extract quarterly data (Revenue, Cost of Sales, SG&A, Adjusted EBITDA) strictly from **Continuing Operations** across 8 quarters (Q1 2024 to Q4 2025) to perform a standardized, "apple-to-apple" trend analysis.
* **The Modern Solution:** Instead of spendings hours opening 8 PDF financial statements, manually searching for footnote adjustments, and typing them into a spreadsheet, you will use **Gemini in Google Sheets** to act as an ingestion engine, accounting cleaner, analyst, and predictive modeler in under 10 minutes.

---

## 2. Learning Objectives

By the end of this lab, you will be able to:
1. **Leverage AI for No-Data-Entry Ingestion:** Connect and extract tabular accounting data directly from PDF files stored in Google Drive using natural language.
2. **Perform Financial Normalization:** Instruct AI to isolate "Continuing Operations" and adjust for discontinued business segments.
3. **Build Dynamic Financial Formulas:** Construct and implement Google Sheets formulas for Quarter-over-Quarter (QoQ) growth, Adjusted EBITDA margin, and Compound Quarterly Growth Rate (CQGR).
4. **Develop Interactive Dashboards:** Generate multi-axis combo charts using natural language and organize your workspace for corporate presentations.
5. **Run Predictive Forecasts:** Create a forward-looking 2026 model comparing statistical linear regression (`TREND`) with compounding growth projection methods.

---

## 3. Lab Prerequisites & Workspace Setup

Before starting, ensure you have:
1. A **Google Workspace** account with access to **Google Drive** and **Google Sheets** (with the **Gemini side panel** enabled).
2. The 8 source PDF files uploaded to a folder in your Google Drive:
   * `2024-Q1-FS.pdf`, `2024-Q2-FS.pdf`, `2024-Q3-FS.pdf`, `2024-Q4-FS.pdf`
   * `2025-Q1-FS.pdf`, `2025-Q2-FS.pdf`, `2025-Q3-FS.pdf`, `2025-Q4-FS.pdf`
3. A new, blank Google Sheet open in your browser.
4. Click the **"Ask Gemini"** button in the top right corner of Google Sheets to open the interactive AI side panel.

---

## 4. Step-by-Step Lab Activities

---

### Phase 1: Zero-Data-Entry Financial Ingestion and Normalization

In this activity, you will instruct Gemini to scan the 8 quarterly earnings PDFs in your Google Drive, extract the correct continuing operations rows, and format them into a structured horizontal table.

```
       [ 8 Unstructured PDFs in Google Drive ]
                         │
                         ▼
        [ Gemini Context-Aware Ingestion ]
           (Filters for Continuing Ops)
                         │
                         ▼
      [ Horizontal Financial Grid in Sheets ]
```

#### Step 1.1: Submit the Ingestion Prompt
In the **Ask Gemini** prompt box at the bottom of the side panel, copy and paste the following master prompt:

> **Master Ingestion Prompt:**
> *"Review the following 8 files in my Google Drive: '2024-Q1-FS.pdf', '2024-Q2-FS.pdf', '2024-Q3-FS.pdf', '2024-Q4-FS.pdf', '2025-Q1-FS.pdf', '2025-Q2-FS.pdf', '2025-Q3-FS.pdf', and '2025-Q4-FS.pdf'. Extract the Revenue, Cost of Sales, SG&A, and Adjusted EBITDA for each quarter. Because the Environmental Services segment was divested in 2025, extract data strictly from Continuing Operations so our 2-year trend is standardized. Organize this into a horizontal table with quarters as columns."*

#### Step 1.2: Preview and Insert Data
1. Hit **Enter** or click the **Send (arrow)** button.
2. Gemini will read through the PDFs in your Drive, resolve the discontinued operations, and render a table preview.
3. Click the **"Insert"** button at the bottom of Gemini's response.
4. This will instantly populate your sheet (cells `A1` to `I5`).

#### Expected Historical Data Baseline:
Verify that your inserted table matches these normalized continuing operations values (figures in millions, $):

| Line Item | Q1 2024 | Q2 2024 | Q3 2024 | Q4 2024 | Q1 2025 | Q2 2025 | Q3 2025 | Q4 2025 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Revenue** | $1,431.8 | $1,556.2 | $1,581.4 | $1,539.0 | $1,452.1 | $1,643.0 | $1,694.2 | $1,686.4 |
| **Cost of Sales** | $1,152.6 | $1,221.6 | $1,235.1 | $1,228.1 | $1,141.4 | $1,260.2 | $1,284.2 | $1,291.8 |
| **SG&A** | $152.3 | $160.1 | $158.5 | $168.2 | $156.4 | $172.5 | $176.1 | $181.2 |
| **Adjusted EBITDA** | $374.4 | $424.6 | $439.4 | $412.5 | $418.2 | $495.2 | $535.1 | $515.0 |

> 💡 **Student Concept Check:** Notice how Revenue drops slightly from Q4 2024 ($1,539.0M) to Q1 2025 ($1,452.1M). This is typical seasonality in environmental services, as cold northern winters slow down construction and solid waste collection volumes. By having a full 8-quarter trend, we can account for these seasonal cycles.

---

### Phase 2: Operational and Margin Analysis

Now that the data is structured, you must analyze GFL's operating efficiency. We want to calculate the Quarter-over-Quarter (QoQ) Revenue growth rate and the Adjusted EBITDA margins.

```
       [ Raw Revenue ] ──► [ QoQ Growth Rate ]  ──► (Measures short-term momentum)
  [ Adjusted EBITDA ] ──► [ Operating Margin ] ──► (Measures profitability efficiency)
```

#### Step 2.1: Submit the Analytical Prompt
In the Gemini panel, type the following:

> **Master Analysis Prompt:**
> *"Based on the sheet data, calculate the Quarter-over-Quarter (QoQ) Revenue growth rate from Q2 2024 to Q4 2025. Also, calculate the Adjusted EBITDA margin for each quarter. Tell me what formulas to use or append them to the table."*

#### Step 2.2: Implement the Formulas in Google Sheets
Gemini will guide you on which formulas to write to keep your model dynamic. Enter these into your sheet:

1. **Adjusted EBITDA Margin:**
   * In cell `B6`, enter: `=B5/B2` (Adjusted EBITDA / Revenue)
   * Format as a percentage (`%`) with 2 decimal places.
   * Drag this formula horizontally from `B6` to `I6` to calculate the margin for all quarters.

2. **QoQ Revenue Growth Rate:**
   * In cell `C7` (Q2 2024 Growth), enter: `=(C2-B2)/B2` (or `=C2/B2 - 1`)
   * Format as a percentage (`%`).
   * Drag this formula horizontally from `C7` to `I7` (Note: `B7` remains blank as Q1 2024 is our baseline).

#### Historical Margin Expansion Analysis:
Review your calculations. You should see a highly significant financial trend:

| Metric | Q1 2024 | Q2 2024 | Q3 2024 | Q4 2024 | Q1 2025 | Q2 2025 | Q3 2025 | Q4 2025 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Adj. EBITDA Margin** | 26.15% | 27.28% | 27.78% | 26.80% | 28.80% | 30.14% | 31.58% | 30.54% |
| **QoQ Rev Growth** | Baseline | +8.69% | +1.62% | -2.68% | -5.65% | +13.15% | +3.12% | -0.46% |

> 📈 **Key Analytical Insight:** Why did Adjusted EBITDA margin expand from **26.15% in Q1 2024** to **31.58% in Q3 2025**? This expansion represents the strategic rationale behind the $8.0 billion divestiture. The Environmental Services segment was lower-margin and capital-intensive. Post-divestiture, GFL became a more focused, high-margin, pure-play Solid Waste company.

---

### Phase 3: Visual Storytelling & Dashboarding

To present your findings to executives or investors, you need to turn these columns of numbers into a highly intuitive, professional chart.

#### Step 3.1: Submit the Chart Prompt
In the Gemini panel, type:

> **Master Chart Prompt:**
> *"Create a combo chart showing the 2-year quarterly Revenue as vertical bars and overlay the Adjusted EBITDA margin expansion as a line trend. Add this chart into another sheet. Rename sheet 1 as 'Analysis' and sheet 2 as 'Dashboard'."*

```
     [ Revenue (Millions $) ]                      [ EBITDA Margin (%) ]
             ┌─┐                                          ●───○  31.58%
             │ │     ┌─┐                           ○───● /
             │ │ ┌─┐ │ │                   ┌─┐    /
         ┌─┐ │ │ │ │ │ │             ┌─┐   │ │   o
         │ │ │ │ │ │ │ │     ┌─┐     │ │   │ │   │
         └───┴─┴─┴─┴─┴─┴─────┴───────┴─────┴───┴─┴──────────────────
        Q1  Q2  Q3  Q4 2024 Q1      Q2    Q3  Q4 2025
```

#### Step 3.2: Structure the Workbook
1. Click **Insert Chart** from Gemini's response to drop the combo chart onto your sheet.
2. In the bottom-left tab menu of Google Sheets, double-click the active sheet tab and rename it to **Analysis**.
3. Click the **"+"** sign to add a new sheet. Double-click to rename it **Dashboard**.
4. Cut (`Cmd+X` or `Ctrl+X`) your new chart from the **Analysis** sheet, switch to the **Dashboard** sheet, and paste it (`Cmd+V` or `Ctrl+V`). Resize it for a clean, executive-ready look.

---

### Phase 4: Transitioning to Predictive FP&A

Corporate financial planning is forward-looking. In this final phase, you will transition from historical reporting to creating a dynamic projection model for all four quarters of 2026.

```
       [ 8-Quarter Historical Baseline ]
                      │
                      ├─► 1. Calculate Compound Growth (CQGR = 2.36%)
                      │
                      ▼
     [ 4-Quarter 2026 Forecast Model ]
        - Projected Revenue (Compounded)
        - Projected Cost of Sales (Average Run-Rate)
```

#### Step 4.1: Submit the Forecasting Prompt
In the Gemini panel, enter:

> **Master Forecasting Prompt:**
> *"Based on the 8-quarter financial model in our sheet (where continuing operations revenue scaled from $1,431.8 million in Q1 2024 to $1,686.4 million in Q4 2025), calculate the Compound Quarterly Growth Rate (CQGR) for revenue. Then, create a projection table for the upcoming quarters of 2026 (Q1 2026 through Q4 2026) in another sheet. Assume Cost of Sales maintains its historical average percentage of revenue, and provide the exact Google Sheets formulas needed to make this dynamic."*

#### Step 4.2: Understanding the Mathematical Logic
Before applying the formulas, let's look under the hood of the math Gemini is performing:

##### 1. Calculating Compound Quarterly Growth Rate (CQGR)
To calculate the true compounded growth rate across GFL's 8 historical quarters (which represents 7 compounding periods of growth from Q1 2024 to Q4 2025), we use:

$$\text{CQGR} = \left( \frac{\text{Ending Value}}{\text{Beginning Value}} \right)^{\frac{1}{n}} - 1$$

$$\text{CQGR} = \left( \frac{1,686.4}{1,431.8} \right)^{\frac{1}{7}} - 1 \approx 2.36\% \text{ per quarter}$$

##### 2. Projecting Cost of Sales (Efficiency Run-Rate Method)
To project Cost of Sales, the AI evaluates the relationship between historical Cost of Sales and Revenue. Over the past 8 quarters, Cost of Sales averaged **~79.8% of Revenue**. To maintain this efficiency run-rate in the future, our formula must multiply each forecasted quarter's Revenue by this average percentage.

#### Step 4.3: Set Up the Forecast Sheet
1. Create a third sheet tab and rename it **Forecast**.
2. Set up your column headers in Row 1:
   * Cell `A1`: `Metric`
   * Cell `B1`: `Q1 2026 (F)`
   * Cell `C1`: `Q2 2026 (F)`
   * Cell `D1`: `Q3 2026 (F)`
   * Cell `E1`: `Q4 2026 (F)`
3. Set up your row labels in Column A:
   * Cell `A2`: `Projected Revenue`
   * Cell `A3`: `Projected Cost of Sales`

#### Step 4.4: Input the Dynamic Sheets Formulas

To ensure your model is fully dynamic (meaning if you update historical numbers, the forecast automatically adjusts), write these formulas in your **Forecast** sheet:

##### For Projected Revenue (Compounded Growth Method):
We reference the last historical quarter, Q4 2025 (which is in cell `I2` on our **Analysis** sheet), and compound it by the $2.36\%$ quarterly rate:
* In cell `B2` (Q1 2026 Forecast), enter:
  ```excel
  =Analysis!I2 * (1 + 0.0236)
  ```
* In cell `C2` (Q2 2026 Forecast), reference the previous forecasted quarter to continue compounding:
  ```excel
  =B2 * (1 + 0.0236)
  ```
* Drag this formula across to cells `D2` and `E2`.

##### Alternative Method: Statistical Linear Trend
If you prefer a purely statistical regression line that fits your historical quarters, you can use Google Sheets' native multivariate statistical formula:
* In cell `B2`, enter:
  ```excel
  =TREND(Analysis!B2:I2, Analysis!B1:I1, "Q1 2026")
  ```
  *(Where `Analysis!B2:I2` is your historical revenue row, and `Analysis!B1:I1` contains your quarter names).*

##### For Projected Cost of Sales (Historical Efficiency Run-Rate):
We project costs by taking the average historical cost-to-revenue ratio and multiplying it by our new projected revenues:
* In cell `B3`, enter:
  ```excel
  =B2 * AVERAGE(INDEX(Analysis!B3:I3 / Analysis!B2:I2))
  ```
* Drag this formula across to cell `E3` (`C3` to `E3`).

#### Expected 2026 Forecast Model Output (Compounded Growth):

| Metric | Q1 2026 (Forecast) | Q2 2026 (Forecast) | Q3 2026 (Forecast) | Q4 2026 (Forecast) |
| :--- | :---: | :---: | :---: | :---: |
| **Projected Revenue** | $1,726.2M | $1,766.9M | $1,808.6M | $1,851.3M |
| **Projected Cost of Sales** | $1,377.5M | $1,409.9M | $1,442.2M | $1,483.9M |

---

## 5. Comprehensive Formulas Reference Sheet

Ensure you understand the syntax and purpose of each formula used in this lab:

| Financial Metric | Mathematical Formula | Google Sheets Formula Example | Why It Matters in FP&A |
| :--- | :--- | :--- | :--- |
| **Operating Margin (EBITDA %)** | $$\frac{\text{Adjusted EBITDA}}{\text{Revenue}}$$ | `=B5 / B2` | Measures how many cents of profit GFL keeps from every dollar of sales. |
| **Quarter-over-Quarter Growth** | $$\frac{\text{Current Q} - \text{Prior Q}}{\text{Prior Q}}$$ | `=(C2 - B2) / B2` | Tracks short-term revenue momentum and seasonality impacts. |
| **Compound Quarterly Growth** | $$\left( \frac{\text{End Value}}{\text{Start Value}} \right)^{\frac{1}{n}} - 1$$ | `=(I2 / B2)^(1/7) - 1` | Smoothes out quarterly volatility to find the true underlying growth rate. |
| **Statistical Linear Trend** | $$\text{Least-Squares Regression Line}$$ | `=TREND(B2:I2, B1:I1, J1)` | Plots a linear best-fit regression line to predict future intervals. |
| **Run-Rate Expense Estimation** | $$\text{Projected Rev} \times \text{Avg Cost Ratio}$$ | `=B2 * AVERAGE(B3:I3 / B2:I2)` | Forecasts future overhead assuming operational efficiency remains stable. |

---

## 6. Student Reflection & Analytical Exercises

To complete your lab, answer the following financial analysis questions based on your model:

1. **Strategic Margin Shift:** In Q1 2024, GFL's Adjusted EBITDA margin was **26.15%**. By Q3 2025, it had reached **31.58%**. Why did GFL experience such substantial margin expansion during this period? How does this connect to the $8.0B divestiture mentioned in the case study?
2. **Growth Methodology Comparison:** Compare your 2026 Revenue projections using the **CQGR method** (compounded growth) versus the **Statistical TREND method** (linear regression). Which method is more conservative? In what economic environments would you use one over the other?
3. **Seasonality and Operational Costs:** Look closely at GFL's Q1 vs. Q3 performance in both 2024 and 2025. What patterns do you notice in operational costs? If you were the CFO, how would you manage cash flow in Q1 to prepare for the surge in Q2 and Q3?

---

## 7. Instructor Demonstration Guide (A Visual "Wow" Lesson)

If you are displaying this workflow live in a lecture, use this quick pacing guide to keep students engaged and drive home the value of AI in finance:

* **The Hooks (Minutes 1-3):** 
  * Open Google Sheets with a completely empty grid.
  * Hold up your phone or point to a stack of papers and say: *"Imagine your boss dumps 8 quarters of financial reports on your desk and asks for an adjusted trend report for a board meeting in 15 minutes. In the past, this meant manual PDF scraping, copying tables, fixing errors, and building charts. Let's see how modern analysts do this."*
* **The "Zero Data Entry" Magic (Minutes 4-6):**
  * Paste the **Master Ingestion Prompt** into Gemini. Point out that the prompt specifically instructs the AI to ignore discontinued operations and isolate **Continuing Operations** due to the $8B transaction.
  * *Instructor Note:* Emphasize that the AI isn't just reading text—it actually understands the accounting structure of the balance sheets and income statements.
  * Click **Insert** and watch the grid instantly fill up with clean data.
* **The Quick Analytics Turn (Minutes 7-8):**
  * Run the **Analysis Prompt**. Have a student write down the EBITDA margins on the board as they calculate. 
  * Highlight the margin jump (26.15% to 31.58%) to explain **corporate rationalization and focusing on core competencies**.
* **The Predictive FP&A Finish (Minutes 9-10):**
  * Generate the **Forecast Model** using CQGR and dynamic average formulas.
  * Show them how the formulas in the forecast cells are **dynamic formulas pointing to the Analysis sheet** rather than hardcoded static numbers.
* **The Closing Statement:**
  * *"We just performed ingestion, structural accounting adjustments, trend margin calculations, interactive data charting, and built a dynamic predictive model in under 10 minutes. By mastering these AI tools, you spend 5% of your time on manual formatting and 95% of your time on strategic financial decision-making."*
