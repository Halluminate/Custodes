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
In the Balance Sheet tab, link PP&E and Long-Term Debt from Capex and Debt Assumptions for Jan-23 to Dec-28. In the Assumptions – Line 01 tab, insert monthly volume distribution (Jan 8.0%, Feb 9.5%, Mar 10.5%, Apr 9.5%, May 6.5%, Jun 7.0%, Jul 7.0%, Aug 7.0%, Sep 8.5%, Oct 9.0%, Nov 9.0%, Dec 8.5%) in blue for all years totaling 100%. In the Dashboard tab, link Line 01, Line 02, and Line 03 segment revenues in millions from FY23–FY28 (convert segmental revenue numbers from absolute numbers to millions). In the Ratio Analysis tab, calculate EBITDA Margin. In the Working Capital tab, calculate Total Net Working Capital.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/08_02_Seafood_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
