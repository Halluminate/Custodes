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
In the Assumption sheet, set Content Writing guest post percentage at 8% Apr-25, increasing 15% in Apr-26 and Apr-27, 10% in Apr-28. Also set Content Writing Cost per unit at 0.50 Apr-25, 0.55 Apr-26, 0.60 Apr-27, 0.70 Apr-28, 0.75 Apr-29. In the DCF sheet, calculate Net Cost of Debt. In the Balance Sheet Schedules, apply 10% annual interest. In the Balance Sheet, calculate Total Liabilities and Equity and validate against Total Assets. In the Employee Expenses sheet, set SEO salary from Apr-25 escalating annually through Mar-30 using Inflation Rate from DCF.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/06_01_DigiMark_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
