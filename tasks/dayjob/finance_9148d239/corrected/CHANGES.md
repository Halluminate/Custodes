# Changes: DAYJOB finance_9148d239

Fix summary (from the fix record):

graderGuidance: c016-c019 also pass when the memo simply does not raise those cleared items as issues.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Undisclosed requirement to write affirmative sign-off commentary on four non-blocking compliant items (c016, c017, c018, c019)
  - Change: graderGuidance: c016, c017, c018 and c019 each keep their wording and gain one clause so that a response that does not raise that item as an issue (CV-1107 broker pricing, Avyra 26 June price, Dravena 1,242.000 CZK price, Prosus/Qatar fallback prices) also satisfies it; wrongly flagging the item still fails.
