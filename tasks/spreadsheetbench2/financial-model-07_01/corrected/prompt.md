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
In the Sales Schedule sheet, implement a scenario selector (in cell F16, Scenarios 1–5, default to scenario 1) that drives all sales calculations including pricing, absorption, collections, and ancillary revenue. In the Cashflow (Quarterly) sheet, align Acquisition Costs with the start dates and durations in Inputs, then in the Cashflow (Monthly) sheet, reconstruct the monthly allocation for all time-bound costs across Years 1–7 based on the same timing parameters. In the Executive Summary sheet, link the year and period labels to the Cashflow (Quarterly) timeline, then reconstruct the Closing Balance for each period in Project Cashflows. In the Cashflow (Monthly) sheet, reconstruct the Prestige Financing recognition based on the Start Date in Inputs. In the Cashflow (Quarterly) sheet, reconstruct Approval Costs for Years 1–5 by aggregating monthly values.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/07_01_RealEstate_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
