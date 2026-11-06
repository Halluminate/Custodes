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

In the ‘Work Sheet’ sheet, calculate for all years the % of total revenue mix, then for all quarters and years from 4QFY24 onwards, calculate all totals from bed capacity to EBITDA % (where ARPOB stands for ‘average revenue per occupied bed’). From 1QFY22 to 3QFY24, inclusive of the yearly breakdown, fill in, or calculate totals where needed for each, the List of Hospitals & Capacity Beds numbers – For State 1: City 1 has 1000 for each quarter and FY, and City 2 has 200; for State 2: City 3 has 250 for each quarter and FY, and City 4 has 180 for the first 3 quarters and 195 for each subsequent quarter and year, and City 5 has 200; for State 3: City 6 has 350 for each quarter and FY, and City 7 has 434 but has 469 for the last 3 quarters, and City 8 has 250 and City 9 has 200; for State 4: City 10 has 290 for each quarter and FY besides the first quarter, and City 11 has 237 for all but the first quarter and City 12 has 75 but just for from 4QFY22 to 3QFY23, inclusive of FY22; for State 5: it’s 334 from 2QFY23 to 3QFY24 inclusive of FY23). EBITDA (calc) needs to be calculated from 4QFY23 onwards and then EBITDAM (calc) from FY23 onwards.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/15_02_KIMS_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
