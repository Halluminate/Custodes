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
In the IRR Calculation sheet, compute Gross IRR and Net IRR for both Fund and LP calculations from Dec-25 to Jun-33. In the IS - Mgmt Co. sheet, calculate totals for all income statement components from Apr-25 to Jun-33. In the Dashboard, update hurdle rate to 12.0%, carry for IRR<30% to 16.0%, and IRR>30% to 20.0%, and update Exit Multiple for second and third tranches to 2.0x for all deals. In the Workings Cost sheet, compute total funds raised for all three tranches from Apr-25 to Jun-33.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/05_01_AIF_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
