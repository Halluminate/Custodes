# Changes: SpreadsheetBench 2 template-14_04

Fix summary (from the fix record):

Full pass: prompt states the Year 1 timing convention the key uses (base year grown one period).

Changed files (in this folder):

- prompt.md

## Fixed

- other finding, major, not in findings.json: Whether Year 1 equals the base year or base year grown one period is never stated, and the binary grader accepts only the grown version
  - Change: Prompt: added 'Year 1 grows the base-year figures by one year of the growth rates.' after the instruction (key: C34 =C18*(1+C$10), C42 =C25*(1+C$11), C44 =C27*C$6*(1+C$13)). Answer key unchanged.
