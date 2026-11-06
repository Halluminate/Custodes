# Changes: GDPval 0419f1c3-d669-45d0-81cd-f4d5923b06a5

Fix summary (from the fix record):

The rubric awarded points for a computed acknowledgement-time value and a Yes/No against the 4-business-hour standard, but the Work Order Log has no acknowledgement timestamps (and no times of day), so the points could only be earned by inventing data. The three acknowledgement rubric lines now also credit stating that the data is unavailable and how the KPI will be tracked, and the main one refuses credit for unsupported values. Full pass: the rubric's undisclosed 2025-04-14 to 2025-07-13 window (which the expert's own 16-order figures do not use) now accepts either that window or calendar Q2, and the rubric cites the real file names.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, critical, not in findings.json: Acknowledgement KPI is graded but its source data is missing
  - Change: grader_guidance.md: the [+2] acknowledgement-KPI line now credits either a value supported by the files or a statement that the Work Order Log lacks acknowledgement timestamps plus how it will be tracked, and says not to credit unsupported values. The [+1] business-hours line now refers to measuring the KPI, and the [+1] Yes/No line also accepts 'cannot be determined from the supplied logs'. No other rubric line changed.
- other finding, major, not in findings.json: Grader guidance enforces an undisclosed exact date filter (2025-04-14 to 2025-07-13) that contradicts the ground truth's full-log calculation and excludes early-April records in the Q2 files
  - Change: grader_guidance.md: the [+2] analysis-period line now credits stating the past quarter as either 2025-04-14 to 2025-07-13 or calendar Q2 2025, and the KPI lines say 'for the stated past-quarter period' instead of 'for 2025-04-14 to 2025-07-13'. The expert's figures (84 h, 4 of 16 = 25%) use all 16 orders (04/03 to 07/01), which the old wording failed. No prompt change.
- other finding, major, not in findings.json: Rubric's rolling analysis window (04/14–07/13) contradicts the ground truth's figures, which use all 16 work orders (calendar Q2)
  - Change: Same guidance change as another finding (not listed): either quarter reading is credited, so the expert's all-16-order figures now meet the rubric.
- other finding, major, not in findings.json: Grading imposes an undisclosed quarter boundary that changes the analysis
  - Change: Same guidance change as another finding (not listed).
- other finding, minor, not in findings.json: Rubric uses underscored file names that differ from the actual Desktop files
  - Change: grader_guidance.md: 'Work_Order_Log.xlsx' and 'Resident_Complaint_Log.docx' now read 'Work Order Log.xlsx' and 'Resident Complaint Log.docx', the names of the staged files.
