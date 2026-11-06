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
In the Ratio Analysis sheet, calculate Net Profit % for FY33–FY39 as Net Profit divided by Gross Income. In the Cash Budget sheet, calculate Base Amount Receivable for FY22 Q1–Q4, FY23 Q4, and FY24 Q1–Q4 by applying the Government Incentive percentage to Total Project Cost. In the Revenue sheet, calculate Adjusted O&M for PIM for FY33–FY39 by applying the Price Index Multiple to Actual O&M cost. In the Cash Flow sheet, calculate Net Cash Generation for FY33–FY39 by summing operating, investing, and financing cash flows. In the Milestones sheet, calculate Cost of Project for Phase I–IV based on work completed percentage.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/18_05_RoadAssets_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
