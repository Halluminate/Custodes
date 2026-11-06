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
In the Milestones sheet, calculate Cost of Project at each milestone (I to IV) by allocating total project cost based on completion percentage. In the P&L sheet, calculate PAT Margin for FY25–FY39 displaying "NM" where Total Income is zero or negative. In the Tax Calculation sheet, calculate Income Tax for FY25–FY39 at 25.17% on positive Taxable Income only, then link results to Tax Expense in the P&L sheet. In the BS sheet, calculate Net Fixed Assets for FY26–FY39, then add a balance sheet integrity check for FY22–FY39 comparing total assets to total liabilities and equity. In the DSCR sheet, calculate Average Cash DSCR across the debt tenor.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/18_01_RoadAssets_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
