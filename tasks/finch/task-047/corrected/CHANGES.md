# Changes: FINCH task-047

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Ambiguous tax calculation for Consolidated Purchase and Pooling columns (35.3% applied to consolidated EBT vs. sum of standalone taxes or tax effect on purchase adjustments)
  - Change: graderGuidance: task-specific note accepting either the reference's flat 35.3% consolidated tax or the sum of company-level taxes (35.3% AT&T incl. purchase adjustments, 43.2% NCR), with net income and EPS consistent.
- other finding, major, not in findings.json: Source workbook has a broken Cash Flow formula in I47 (=-(I20+I23) instead of =-(I18+I23)) and misleading row labels/formatting on Row 20 vs Row 23 that conflict with GT edits
  - Change: graderGuidance: same note accepts the $9M in row 20 or 23 and I47/I49 either unchanged or corrected, not counted as error or over-edit.
- other finding, major, not in findings.json: Combined-column income tax uses a flat 35.3% even though the row label gives a separate rate for each company
  - Change: graderGuidance: same task-specific note (either tax treatment accepted).
- other finding, major, not in findings.json: Starter cash-flow formula points at the wrong row and the GT quietly fixes it; the extra-depreciation rows are laid out ambiguously
  - Change: graderGuidance: same task-specific note (I47 either way, $9M in row 20 or 23).
- other finding, major, not in findings.json: Seeded cash-flow formula omits goodwill amortization
  - Change: graderGuidance: same task-specific note (I47/I49 accepted unchanged or corrected).
