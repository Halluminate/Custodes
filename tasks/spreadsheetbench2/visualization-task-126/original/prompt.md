<task_context>

## Important
- When completing spreadsheet tasks, strictly avoid altering any cells that already contain values unless explicitly instructed. Modify only the cells that are required for the task.
- You need to complete the instructions and ensure that the original formatting is preserved as much as possible.

## Environment
You can complete spreadsheet visualization tasks using the following Python environment:
- `openpyxl`
- `xlsxwriter`

Your task scope **only includes visualization-related operations**, specifically:
- **Chart creation**
- **Pivot table construction**

## Task Objective (Critical)
Your goal is to create **clear, professional, and interpretable visualizations** from the given spreadsheet.
This includes:
- Selecting **appropriate chart or pivot table types** based on the data semantics
- Ensuring the visualization **accurately reflects the underlying data**
- For such unsupported types, we approximate the intended visualization using alternative chart forms that achieve similar visual or structural effects.
- Producing outputs that would be considered **presentation-ready in a professional or analytical context**

A correct solution is not only functionally valid, but also **visually reasonable and well-designed**.

## Recommended Workflow
1. **Inspect**: Inspect the data with Python (e.g. openpyxl) to understand the structure and contents of the spreadsheet: list the sheets, then view the sheet contents you need.

2. **Plan**: You must plan your approach to solve the visualisation task.
  - Whether the task requires a **Chart** or a **Pivot Table**
  - The **chosen visualization type** (e.g., line, bar, scatter, stacked, pivot layout)
  - The **mapping** between data fields and visual elements
    (e.g., x-axis, y-axis, series, categories, values)
  - Any **design considerations** that improve clarity
    (e.g., axis labels, titles, legend placement, sorting, aggregation)

3. **Implement**: Create a python script (e.g., `process_data.py`) that performs the edit.

4. **Execute**: Run the python script using `python3 /tmp/script.py`

5. **Verify**: Check the output file exists, ensure the answer is correct.
   - Ensure the existing structure, layout, and formatting of the model are preserved throughout the process.

6. **Finish**: When verification is successful, stop.

</task_context>

<instructions>

## Task instructions
You need to process a spreadsheet file based on specific instructions.
**Instruction:** Create 2 Earnings Per Share charts using the provided dataset in the Surprise sheet (rows 50-71). The first chart is a multi-series combo chart shown by quarter. The primary Y-axis tracks EPS values and the secondary Y-axis tracks Price. Title the chart "Quarterly Price Impact Analysis" at the top center. Display 4 series: Differential (as overlay floating bars spanning from Mean to After Event for each period), After Event (line), Mean (Estimated Value) (markers only), and Price (line on secondary axis). The second chart is a diverging vertical column chart showing Price Impact (%) by quarter, titled "Earnings Per Share: Actual vs. Estimated Performance" at the top center. Both charts should display quarters from Q3 2020 to Q3 2025 on the X-axis.

## Input and Output
You are provided with an input spreadsheet file, and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/Task 126_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
