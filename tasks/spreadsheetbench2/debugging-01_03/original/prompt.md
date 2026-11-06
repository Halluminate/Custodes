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
**Instruction:** Please audit and fix this file thoroughly. Errors may include but are not limited to: deleted rows causing #REF! errors, broken cross-sheet references, typos in sheet names, and cascading calculation failures. Fixes must be applied in the correct order - restoring structural elements before fixing dependent formulas.

Reference data: The model uses 3 scenario cases (Base, Upside, Downside). The active scenario case selector value is 3.

Note: After fixing all formulas, the debt schedule and sensitivity tables may still show #REF! due to stale cached values from the circular reference. To resolve: click any #REF! cell in the debt schedule, press F2 then Enter to force recalculation, then press Ctrl+Alt+F9 (or Cmd+Option+F9 on Mac) several times to let the iterative calculation converge.

## Input and Output
You are provided with an input spreadsheet file and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/Errors_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
