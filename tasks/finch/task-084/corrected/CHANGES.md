# Changes: FINCH task-084

Fix summary (from the fix record):

Grader guidance task note: states the regression the reference computes, and accepts any labeling of the coefficient and intercept columns (the reference puts the Xerog label over the intercept column) and no AC24 leftover.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: grader_guidance.md: added a task note after the opening paragraph naming the reference's LINEST block (Q6:Q227 on R6:R227, coefficient column then intercept column with their values), saying its labels are misplaced and AC24's 1 is a leftover, and accepting any header labels for the two value columns (the instruction's Xerog/NBSK in either order, or coefficient/intercept) as long as the five statistic rows are correct.
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: grader_guidance.md: added a task note after the opening paragraph naming the reference's LINEST block (Q6:Q227 on R6:R227, coefficient column then intercept column with their values), saying its labels are misplaced and AC24's 1 is a leftover, and accepting any header labels for the two value columns (the instruction's Xerog/NBSK in either order, or coefficient/intercept) as long as the five statistic rows are correct.
- other finding, major, not in findings.json: Ground truth puts the X-variable label over the intercept column, not the slope column
  - Change: grader_guidance.md: added a task note after the opening paragraph naming the reference's LINEST block (Q6:Q227 on R6:R227, coefficient column then intercept column with their values), saying its labels are misplaced and AC24's 1 is a leftover, and accepting any header labels for the two value columns (the instruction's Xerog/NBSK in either order, or coefficient/intercept) as long as the five statistic rows are correct.
- other finding, major, not in findings.json: Prompt asks for column headers 'Xerog' and 'NBSK', which does not fit a regression output table
  - Change: grader_guidance.md: added a task note after the opening paragraph naming the reference's LINEST block (Q6:Q227 on R6:R227, coefficient column then intercept column with their values), saying its labels are misplaced and AC24's 1 is a leftover, and accepting any header labels for the two value columns (the instruction's Xerog/NBSK in either order, or coefficient/intercept) as long as the five statistic rows are correct. The prompt is unchanged (the grading note removes the header conflict).
- other finding, minor, not in findings.json: Unexplained value '1' left in the ground-truth table
  - Change: grader_guidance.md: added a task note after the opening paragraph naming the reference's LINEST block (Q6:Q227 on R6:R227, coefficient column then intercept column with their values), saying its labels are misplaced and AC24's 1 is a leftover, and accepting any header labels for the two value columns (the instruction's Xerog/NBSK in either order, or coefficient/intercept) as long as the five statistic rows are correct. The note says the AC24 value is a leftover and is not required.
