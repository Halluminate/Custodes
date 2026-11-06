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
In the Balance Sheet, calculate CAGR for each Asset line item over FY08–FY13 and FY13–FY18F, then calculate Risk Factor for all historical periods holding FY13 constant for forecast years. In the Balance Sheet Valuation Matrix, calculate Basic EPS for FY08–FY13. In the Income Statement, calculate year-on-year growth for all line items. In the Cash Flow Statement, populate opening Cash and Cash Equivalents linking FY14 from the Balance Sheet and FY15–FY18 sequentially. In the Valuation section (Method 1: EVA), calculate Required Equity for FY14–FY18F at a 10% Tier 1 Capital Ratio.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/03_01_Banking_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
