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
In the Dashboard, update ticket size per investment for first, second, and third tranches at 20, 10, and 10 in light blue, and compute investment exit value for each tranche. In the Workings Cost sheet, compute ending PP&E from Apr-25 to Jun-33. In the CF sheet, link Change in Working Capital. In the Distribution Sheet – Deal By Deal, link hurdle rate from Dashboard. In the Other Expense sheet, compute total expenses for Y2 and Y3.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/05_04_AIF_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
