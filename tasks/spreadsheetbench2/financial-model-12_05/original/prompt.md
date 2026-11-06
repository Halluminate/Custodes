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
In the Working Capital sheet, calculate NWC as a percentage of Revenue for Mar-20 to Mar-30. In the Ratio Analysis sheet, calculate Asset Turnover Ratio for FY20–FY30E. In the Chart sheet, create a combo chart for FY21–FY30E showing Net Profit as columns and Net Profit Margin as a line on a secondary axis. In the Comps sheet, calculate EV/Revenue for Comparable 2 for FY19–FY23, then EV/EBITDA for Comparable 4 for FY19–FY23 only, then P/E for Comparable 6 for FY19–FY23 only.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/12_05_Infra_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
