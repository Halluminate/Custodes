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
**Instruction:** Complete the AIF financial model based on the provided assumptions. Ensure the existing structure, layout, and formatting of the model are retained throughout the process.
In the Dashboard, update Committed Capital for 1st, 2nd, and 3rd Close at 40, 130, and 80 in light blue. In the Workings Cost sheet, derive the year from dates for Apr-25 to Jun-33, then calculate salary per month with annual increases for all designations. Start the monthly salaries in column N at 200,000, 150,000, 100,000 and 50,000 for Designated Partners, Head of Operations, Analyst and Associate, scaled to the sheet's units as =200000/10^5 and so on, and at 0 for General Support and Senior Associate. In the CF sheet, compute totals for operating, investing, and financing cash flows. In the IRR Calculation sheet, link investment amounts for each close from Dashboard. In the Revenue sheet, compute cumulative exits from periodic exits.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/05_05_AIF_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
