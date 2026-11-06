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
**Instruction:** Complete the bond accounting model. Calculate the implied discount rate (IRR of provided cash flows), amortization schedule, tax impacts, and early extinguishment gain/loss. Put the implied discount rate in J9. Enter the coupon payment in row 8 as a positive amount and the premium amortization in row 7 as a negative amount (effective-interest expense less the coupon). For tax purposes, the bond stays at its $15,825 issue price until it is repaid, so the full $825 premium is taxed as a gain on extinguishment in 2023. In the Tax Balance Sheet, Cash Impact shows only the $15,000 principal repaid in 2023, as a negative amount.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/01_08_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
