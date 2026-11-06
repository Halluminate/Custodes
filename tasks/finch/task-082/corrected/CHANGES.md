# Changes: FINCH task-082

Fix summary (from the fix record):

Guidance note scopes grading to the correlation values and header paper types, so the reference's header offset and mixed number formats no longer swing the grade.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: appended to the opening paragraph 'Task note: judge the correlation values (NBSK against each paper's monthly price column) and that the headers name the same paper types as the left table; accept headers mirrored from any of the left table's header rows and any placement of the table on 'simplecorr', and do not fail an output, the reference included, for number precision, bold or column width.'
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: appended to the opening paragraph 'Task note: judge the correlation values (NBSK against each paper's monthly price column) and that the headers name the same paper types as the left table; accept headers mirrored from any of the left table's header rows and any placement of the table on 'simplecorr', and do not fail an output, the reference included, for number precision, bold or column width.'
- other finding, minor, not in findings.json: Ground-truth header block is shifted down a row and leaves out the left table's actual column-label row
  - Change: graderGuidance: appended to the opening paragraph 'Task note: judge the correlation values (NBSK against each paper's monthly price column) and that the headers name the same paper types as the left table; accept headers mirrored from any of the left table's header rows and any placement of the table on 'simplecorr', and do not fail an output, the reference included, for number precision, bold or column width.'
- other finding, minor, not in findings.json: GT correlation table renders with inconsistent number formats and cut-off headers
  - Change: graderGuidance: appended to the opening paragraph 'Task note: judge the correlation values (NBSK against each paper's monthly price column) and that the headers name the same paper types as the left table; accept headers mirrored from any of the left table's header rows and any placement of the table on 'simplecorr', and do not fail an output, the reference included, for number precision, bold or column width.'
