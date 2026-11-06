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

In the Formats sheet, after linking all elements of the first Consolidated Financials table to a different tab, calculate net margin (%) for all historical and forecasted years. Then, in the balance sheet of the Consolidated Financials table, calculate the efficiency ratios and leverage ratios for all years, note that some ratios might require referencing from other tabs as part of their calculation. Also in the Formats sheet, create logical functions below the consolidated Quarterly Result Table that are related to the % change in the following elements of the table: Net Sales, EBITDA, PBT, Recurring PAT, Gross Margin, EBITDA Margin, and PAT Margin. For the outputs of the elements that pertain to 3QFY23 and 2QFY24, the logical function should produce a ‘+’ sign if it’s above 0, and a ‘–’ sign if not. And for the outputs of the elements that pertain to 3QFY24E, the logical function should produce the word ‘ahead’ if it’s above 0, and the word ‘below’ if not. Then, in the Report Tables sheet, link all elements of the Particulars table to the corresponding elements found in the Formats sheet, but for the Cost items as % of sales (including % Change) and the % Change part of the Margin (%) section, calculate the numbers – note: for the % change of those 2 sections, the measurement is ‘bps’.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/15_05_KIMS_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
