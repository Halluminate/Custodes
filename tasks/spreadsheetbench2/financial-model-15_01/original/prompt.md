<task_context>

## Important
- When completing spreadsheet tasks, strictly avoid altering any cells that already contain values unless explicitly instructed. Modify only the cells that are required for the task.
- You need to complete the instructions and ensure that the original formatting is preserved as much as possible.

## Environment
You can complete the corresponding spreadsheet tasks using the following Python environment:
`Pandas`, `openpyxl`, `numpy` and `LibreOffice`
You can use these environments to manipulate the spreadsheet data.

## Recommended Workflow
1. **Inspect**: Inspect the data with Python (e.g. openpyxl) to understand the structure and contents of the spreadsheet: list the sheets, then view the sheet contents, formulas and values you need.

2. **Plan**: Decide how to manipulate the data using `openpyxl` or `LibreOffice`.

3. **Implement**: Create a python script (e.g., `process_data.py`) that performs the edit.

4. **Execute**: Run the python script using `python3 /tmp/script.py`

5. **Verify**: Check the output file exists, ensure the answer is correct.
   - Ensure the existing structure, layout, and formatting of the model are preserved throughout the process.

6. **Finish**: When verification is successful, stop.

</task_context>

<instructions>

## Task instructions
You need to process a spreadsheet file based on specific instructions.
**Instruction:** Complete the financial model based on the provided assumptions. Ensure the existing structure, layout, and formatting of the model are preserved throughout the process.

In the Work Sheet sheet, calculate the Occupied Beds for all segments from 4QFY24 onwards (both quarterly and annual), where possible, and then calculate the total Occupied Beds for the same time period in the State 1 section. Then, perform the same task for EBITDA. Subsequently, calculate Total Revenues (inc. Other Income) and Total EBITDA (inc. Other Income) for all time periods. After, in the Consol_annual sheet, for all sections part of Cash Flow Statement (concise), calculate the Net Cash, then calculate capital employed, and non-cash working capital (excl. debt) in the non-concise balance sheet section for all possible years. In the Consol_quarterly sheet, populate the quarterly data for Net Sales by referencing another tab, and then calculate Gross Profit and Gross Margin and then EBIT and Operating Margin. Following this, after referencing another tab for Income Tax Expense (Gain), calculate the tax rate (%) for all quarters. Then in the IS_BS_CF sheet, calculate all Total Equity & Liabilities and Total Assets for each year and for any quarter that has data, and then for every year (not quarter) from 2021 onwards, calculate the Minority Interest in the income statement section. Following this, in the assumptions section of the IS_BS_CF sheet, calculate the working capital cycle for all years. Finally, in the Formats sheet, populate all valuation ratios part of the Cash Flow table.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/15_01_KIMS_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
