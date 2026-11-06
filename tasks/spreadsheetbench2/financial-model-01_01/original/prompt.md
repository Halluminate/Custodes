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
In the Consolidated P&L sheet, calculate the CAGR of Total Revenue from 2025 to 2030. In the Revenue Drivers sheet, reference actual Other Revenue from another tab, and then hardcode the % of Operating Revenue for the forecasted years as the same value as the last actual year’s value. From that, calculate forecasted Other Revenue. Compute operational costs for each Foundation Course line item in the cost drivers. In the Working Capital Schedule sheet, calculate changes in Working Capital for the forecast period using a roll-forward approach based on period-to-period movements in trade receivables, inventory, and trade payables. In the Fixed Assets Schedule sheet, compute depreciation by applying the 25% assumption to opening balance plus capital expenditure for the forecast period. In the Consolidated BS sheet, add a validation check for each year.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/01_01_Education_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
