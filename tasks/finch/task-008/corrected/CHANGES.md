# Changes: FINCH task-008

Fix summary (from the fix record):

Major/minor pass: one grader-guidance task note covering the hidden severity-score method (critical sp-0), the debatable shutdown list, mixed duration conventions, source-dependent loss figures, the mid-shutdown Speaker change and the None/– placeholders.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Undisclosed component scoring formula for 'Overall Severity Score' in Subtask 4 (Sheet5_Impact_Classification)
  - Change: graderGuidance task note item (1): states the reference's max-normalised scoring and accepts any consistent component method within the 40/30/30 maxima, with Overall Impact Classification checked against the agent's own scores. Also covers critical sp-0, which had no prepared fix.
- other finding, major, not in findings.json: Overall Severity Score formula is never given, but the answer key uses a hidden max-normalisation
  - Change: graderGuidance task note item (1): states the reference's max-normalised scoring and accepts any consistent component method within the 40/30/30 maxima, with Overall Impact Classification checked against the agent's own scores. Also covers critical sp-0, which had no prepared fix.
- other finding, major, not in findings.json: Severity-score calculation requires an undisclosed normalization rule
  - Change: graderGuidance task note item (1): states the reference's max-normalised scoring and accepts any consistent component method within the 40/30/30 maxima, with Overall Impact Classification checked against the agent's own scores. Also covers critical sp-0, which had no prepared fix.
- other finding, major, not in findings.json: The answer key's set of 'officially recorded' shutdowns is debatable, and every derived sheet depends on it
  - Change: graderGuidance task note item (2): accepts adding the 1984-09-30 gap and/or the 2018-02-09 lapse, or dropping the 1980 FTC lapse, with derived sheets following the agent's list.
- other finding, major, not in findings.json: Local reference omits shutdown events required by the coverage instruction
  - Change: graderGuidance task note item (2): accepts adding the 1984-09-30 gap and/or the 2018-02-09 lapse, or dropping the 1980 FTC lapse, with derived sheets following the agent's list.
- other finding, major, not in findings.json: GT Duration column mixes counting conventions and does not follow its own Start/End dates
  - Change: graderGuidance task note item (3): accepts End-Start, full-lapse-day, or reference durations when one convention is used consistently.
- other finding, major, not in findings.json: Estimated-loss figures have several valid sources, but the grader expects the GT's numbers
  - Change: graderGuidance task note item (4): accepts furloughed/loss figures from a recognized official source (CBO, OMB) instead of the reference's numbers.
- other finding, minor, not in findings.json: Historical inaccuracy in ground truth for Speaker of the House during the 2018-2019 shutdown (Row 21)
  - Change: graderGuidance task note item (5): accepts Paul Ryan, Nancy Pelosi or both for the 2018-12-22 shutdown.
- other finding, minor, not in findings.json: Leaders listed for the 2018-19 shutdown ignore the change of Speaker mid-shutdown
  - Change: graderGuidance task note item (5): accepts Paul Ryan, Nancy Pelosi or both for the 2018-12-22 shutdown.
- other finding, minor, not in findings.json: Ground truth in Sheet4_Data_Validation and Sheet5_Impact_Classification contradicts prompt formatting rules for missing values ('None' and blanks vs '–')
  - Change: graderGuidance task note item (6): the instruction's 'None' and '–' are accepted as equally correct to the reference's blanks and hyphen.
- other finding, minor, not in findings.json: GT ignores the prompt's literal output conventions ('–' placeholder, "None" text)
  - Change: graderGuidance task note item (6): the instruction's 'None' and '–' are accepted as equally correct to the reference's blanks and hyphen.
