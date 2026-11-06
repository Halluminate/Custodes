# Changes: GDPval c657103b-b348-4496-a848-b2b7165d28b2

Fix summary (from the fix record):

The prompt now starts RMDs at age 75 (2035), matching SECURE 2.0 for a client born in 1960, the rubric and the answer key, and no longer names a template file that is not provided. The conversion-tax rubric item now accepts any stated rate in the prompt's 32%–35% range instead of exactly 35%.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- [F3](../findings.json) (Task Spec): Direct contradiction between task statement (RMDs begin at age 72) and grader guidance / ground truth (RMDs begin in 2035 at age 75)
  - Change: prompt.md: 'Begin year end RMD 12/31 calculation in the year client turns 72.' -> '... turns 75.' (GT and rubric already use 2035, age 75, which is the SECURE 2.0 start age for a client born in 1960).
- [F1](../findings.json) (Verification): The prompt puts the first RMD at age 72, but the rubric and ground truth put it at age 75 (2035)
  - Change: Same prompt RMD-age change as F3.
- [F5](../findings.json) (Task Spec): Grader requires RMDs three years later than the task instructs
  - Change: Same prompt RMD-age change as F3.
- [F2](../findings.json) (Environment & Infra): The 'business digital tunnel' PowerPoint template the prompt requires is not provided
  - Change: prompt.md: 'Utilize the business digital tunnel PowerPoint template ...' -> 'Utilize a business-appropriate PowerPoint template ...', since the template file is not provided (rubric already grades 'an appealing business-appropriate template').
- [F4](../findings.json) (Environment & Infra): Required Business Digital Tunnel PowerPoint template is missing
  - Change: Same prompt template change as F2.
- other finding, major, not in findings.json: Undisclosed constraint requiring exact 35% marginal tax rate when prompt specifies a 32%-35% range
  - Change: graderGuidance: the rubric item '[+2] ... using a marginal tax rate of 35%.' now reads '[+2] For each conversion year, the model calculates tax on the conversion using a stated marginal tax rate within the client's 32%–35% bracket range (the expert uses 35%).' The prompt and assumptions docx give only the 32%–35% range. Not re-graded locally (GDPval pairwise AI grader).
- other finding, major, not in findings.json: The rubric requires a flat 35% tax rate, but the prompt gives a 32%–35% range, and that range does not fit $200k MFJ income
  - Change: Same rubric item change as another finding (not listed) (any stated rate within the given 32%–35% range earns the item).
- other finding, major, not in findings.json: Grader silently narrows the permitted conversion tax rate to 35%
  - Change: Same rubric item change as another finding (not listed).
