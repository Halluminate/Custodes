# Changes: FINCH task-075

Fix summary (from the fix record):

Added the missing Total Scheduled and Total Cancellation series to the reference chart, so the answer key now plots all eight series the prompt asks for. Nothing else in the workbook changed. Prompt example no longer gives the $35MM answer, and the guidance accepts the instructed Dec-98 start and vertical Nov-2001 line where the reference differs.

Changed files (in this folder):

- prompt.md
- grader_guidance.md
- reference/gt_75_ref_0.xlsx

## Fixed

- [F2](../findings.json) (Verification): Ground-truth workbook (gt_75_ref_0.xlsx) omits the required Total Scheduled and Total Cancellation chart series
  - Change: gt_75_ref_0.xlsx xl/charts/chart1.xml: added series 7 'Total Scheduled Payments' ('Cost Cancel Details'!$D$123:$BB$123, solid black) and series 8 'Total Cancellation Payments' ('Cost Cancel Details'!$D$124:$BB$124, dashed black), same category range D3:BB3 as the existing six series. All other parts of the file are byte-identical.
- [F1](../findings.json) (Verification): The ground-truth chart leaves out the required Total Scheduled and Total Cancellation series
  - Change: Same chart fix: the reference chart now includes the GRAND TOTALS rows 123/124.
- other finding, critical, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: The low ground-truth grade came from the missing total series; fixed by the same chart change in gt_75_ref_0.xlsx.
- other finding, major, not in findings.json: Prompt specifies monthly chart data from Dec-98 through Dec-02 ($F$3:$BB$3), whereas the ground-truth chart references Oct-98 through Dec-02 ($D$3:$BB$3)
  - Change: graderGuidance: added task note sentence telling the judge to accept series starting at Oct-98 (as the reference) or Dec-98 (as the instruction says).
- other finding, major, not in findings.json: The stated chart date range differs from the GT's category range, and the 'Nov-2001' column is actually dated 21-Nov-01
  - Change: Same guidance sentence (either start month accepted).
- other finding, major, not in findings.json: Prompt requires a 'blue vertical line at Nov-2001', whereas gt_75_ref_0.xlsx contains two horizontal blue connector arrows and no vertical line
  - Change: graderGuidance: added one sentence noting the reference uses horizontal blue arrows and that a vertical blue line at Nov-2001, as instructed, is accepted.
- other finding, major, not in findings.json: The instruction's example gives away the main graded annotation value ($35MM)
  - Change: prompt.md: the example '(e.g., $35MM)' changed to '(e.g., $XXMM)', so the format stays shown but the graded Nov-01 gap is no longer given.
