# Changes: FINCH task-146

Fix summary (from the fix record):

The key uses Sea/Shopee's Q4 2024 figures, which Sea released on March 4, 2025, after the prompt's February 28 source cutoff. Moved the cutoff to March 31, 2025. That admits Sea's release and changes nothing for Amazon, eBay or Alibaba, whose Q4 releases all came out in February. Full pass: the prompt now says Alibaba's Q1-Q4 are the calendar-2024 quarters, and the guidance accepts a consistent Shopee/Sea scope, eBay's unrounded revenue, and any consistent Validation Status / issue rule.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- [F2](../findings.json) (Verification): Sea/Shopee Q4 2024 figures are in the answer key, but they were published after the stated cutoff
  - Change: Prompt [Data Source Note]: 'published before February 28, 2025' changed to 'published before March 31, 2025', so the key's Shopee Q4 values (GMV 28.6, revenue 3.7, net profit 0.24) are inside the allowed sources.
- [F1](../findings.json) (Verification): Reference requires Sea Q4 results published after the permitted source cutoff
  - Change: Same prompt date change.
- other finding, major, not in findings.json: Undisclosed definition and calculation rules for 'Validation Status' and 'issues' in Subtask 4 (Sheet5_Data_Validation)
  - Change: graderGuidance: appended 'The statement does not define Validation Status or what counts as an issue in the Quality Score, so accept any reasonable status labels and issue rule the agent applies consistently, with Quality Score and Quality Grade following from them.'
- other finding, major, not in findings.json: Sheet5 'Validation Status' and the '-5 per issue' rule are never defined
  - Change: graderGuidance: appended 'The statement does not define Validation Status or what counts as an issue in the Quality Score, so accept any reasonable status labels and issue rule the agent applies consistently, with Quality Score and Quality Grade following from them.'
- other finding, major, not in findings.json: Ambiguity between Shopee segment revenue and Sea Limited consolidated net profit in 'Shopee (Sea)' RawData and downstream metrics
  - Change: graderGuidance: appended to the opening paragraph 'Reference notes for this task: the reference pairs Shopee segment GMV and revenue with Sea Limited's consolidated net income, so also accept Shopee (Sea) figures taken at one consistent scope (Sea consolidated, or Shopee segment with net profit marked unavailable) when the downstream metrics follow from the agent's own RawData.'
- other finding, major, not in findings.json: The Shopee (Sea) row mixes Shopee-segment revenue and GMV with Sea Ltd consolidated net income
  - Change: graderGuidance: appended to the opening paragraph 'Reference notes for this task: the reference pairs Shopee segment GMV and revenue with Sea Limited's consolidated net income, so also accept Shopee (Sea) figures taken at one consistent scope (Sea consolidated, or Shopee segment with net profit marked unavailable) when the downstream metrics follow from the agent's own RawData.'
- other finding, major, not in findings.json: Reference silently combines Shopee segment revenue with Sea consolidated profit
  - Change: graderGuidance: appended to the opening paragraph 'Reference notes for this task: the reference pairs Shopee segment GMV and revenue with Sea Limited's consolidated net income, so also accept Shopee (Sea) figures taken at one consistent scope (Sea consolidated, or Shopee segment with net profit marked unavailable) when the downstream metrics follow from the agent's own RawData.'
- other finding, major, not in findings.json: Alibaba 'FY2024' conflicts with the calendar-2024 quarters used in the GT (contradictory requirements / prompt ambiguity)
  - Change: prompt [Data Source Note]: added after the Alibaba net-income sentence 'For Alibaba, whose fiscal year ends in March, report the calendar-2024 quarters (ending March, June, September and December 2024) as Q1-Q4.' (matches the key: Q1 30.73/0.13 is the March-2024 quarter).
- other finding, minor, not in findings.json: GT rounds eBay revenue to 1 dp, so eBay revenue growth comes out as 0.00% and the ratios drift
  - Change: graderGuidance: appended 'The reference rounds eBay revenue to 2.6 in every quarter, so eBay revenue taken from the reported figures (about 2.56, 2.57, 2.58, 2.58 USD bn) and the margins and Q1-Q4 revenue growth (about 0.9%) that follow from it are also correct.'
