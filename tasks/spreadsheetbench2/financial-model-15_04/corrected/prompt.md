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

In the Consol_annual sheet, calculate (or reference where required) all elements from PBT to EPS Growth (%) for all years. Then, in the Ratios and Growth Analysis section, calculate all elements that are not hardcoded for all years from 2013-2027 – note that for the shares section, for 2023-2027, the numbers for all 5 years should be the same as the last historical year of data. In that section, take Total Invested Capital as Total Debt + Minority Interest + Total Equity - Cash and Capital Employed as Total Debt + Minority Interest + Total Equity, compute Core RoIC and RoIC as (Net Income Before Extraordinaries + Interest Expenses x (1 - Tax rate)) over the average of the prior and current year's Total Invested Capital and Capital Employed respectively, and ROCE as EBIT over average Capital Employed (using the current year alone in 2013), and show growth rates as 0 where there is no prior year. At the end of the tab, calculate the two Check balance lines. In the Consol_quarterly sheet, after referencing for Interest Expenses and Other Non-operating Income (Expense) for all quarters, calculate or reference all elements from PBT to EPS.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/15_04_KIMS_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
