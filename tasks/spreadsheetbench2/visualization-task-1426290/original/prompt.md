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
**Instruction:** Based on the daily patrol times, calculate the average patrol duration for each day and place it in a new "Average" column at the end of that day's row. Identify all durations strictly greater than the daily average and display them in red text. For each of these above-average durations, apply a soft orange fill to the corresponding start time, finish time, and duration cells.

In a new "Avg. Excess Duration" column (next to "Average"), calculate the average of only the above-average durations for that day.

Create a new sheet named "Graph Average Patrol Time" containing:

1. A helper table with dates as column headers and the following as row labels:
   - Date (in DD-MMM format)
   - Average Patrol Time
   - Ideal Average Time (constant 30 minutes)
   - Avg. Excess Duration
   - Count Above Average (count of durations exceeding the daily average)

2. A combo chart positioned below the helper table with:
   - Three line series (straight lines with markers):
     - Average Patrol Time (blue)
     - Ideal Average Time (orange)
     - Avg. Excess Duration (green)
   - One bar series on a secondary Y-axis:
     - Count Above Average (gray)

3. Chart title "Patrol Duration Overview" at top center, legend at bottom.
4. X-axis for dates, primary Y-axis for durations, secondary Y-axis for count.

## Input and Output
You are provided with an input spreadsheet file, and you need to generate an output spreadsheet file based on the output_path.
**Input File:** /home/model/Desktop/Task 1426290_input.xlsx
**Output Path:** /home/model/Desktop/output.xlsx

</instructions>
