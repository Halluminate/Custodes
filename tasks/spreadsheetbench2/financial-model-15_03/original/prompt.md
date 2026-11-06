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

In the IS_BS_CF sheet, in the income statement section, calculate total employee cost and % of sales just for the quarterly data, from Q4 2023 onwards, then calculate Other expenses and % of sales (but here calculate the quarterly data from Q1 2024 onwards), subsequently calculate total non operating (income) / expense for all years and quarters, and then EPS after exceptional items for all years and quarters. Additionally, from FY2024-FY2027, but not for the quarters, calculate all parts of Equity & Liabilities as well as Assets in the balance sheet section – make sure that the Check section is balanced after all calculations. Then, in the assumptions section, fill in all sections from Repayment/(Taken) onwards for all years where there is no hardcoded data, but don’t populate any quarters, just the yearly data (note: to calculate depreciation from 2024-2027, take it as an average of the current year and the previous year’s gross block and multiply it by the current year’s average depreciation).

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/15_03_KIMS_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
