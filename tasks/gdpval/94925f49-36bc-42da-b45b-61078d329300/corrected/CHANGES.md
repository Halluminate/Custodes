# Changes: GDPval 94925f49-36bc-42da-b45b-61078d329300

Fix summary (from the fix record):

The prompt names Garden City Park School but the rubric and expert PDF cover New Hyde Park Road School. I added one guidance sentence telling the grader to apply the New Hyde Park Road School items to whichever of the two schools the agent covers. The blocked-web findings are infra. Full pass: the prompt now says the agent works for Mort Realty and should use the Desktop logo; the guidance treats five per-school reports of up to 10 pages as meeting the length and side-by-side items, credits home listings, gifted % and teacher salary the expert omitted, and accepts equivalent ratings from a source other than Niche.com.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- [F2](../findings.json) (Verification): Grader guidance and ground truth evaluate 'New Hyde Park Road School' instead of the prompt's required 'Garden City Park School'
  - Change: graderGuidance: appended one sentence to the opening paragraph: "The statement asks for Garden City Park School as the fifth school, while the expert deliverable and rubric cover New Hyde Park Road School, so apply every New Hyde Park Road School item to whichever of the two the agent reports on, and do not mark the agent down for covering Garden City Park School."
- [F3](../findings.json) (Verification): Rubric grades 'New Hyde Park Road School', but the prompt asks for 'Garden City Park School'
  - Change: graderGuidance: appended one sentence to the opening paragraph: "The statement asks for Garden City Park School as the fifth school, while the expert deliverable and rubric cover New Hyde Park Road School, so apply every New Hyde Park Road School item to whichever of the two the agent reports on, and do not mark the agent down for covering Garden City Park School."
- [F4](../findings.json) (Reward): Grader substitutes New Hyde Park Road School for the required Garden City Park School
  - Change: graderGuidance: appended one sentence to the opening paragraph: "The statement asks for Garden City Park School as the fifth school, while the expert deliverable and rubric cover New Hyde Park Road School, so apply every New Hyde Park Road School item to whichever of the two the agent reports on, and do not mark the agent down for covering Garden City Park School."
- other finding, major, not in findings.json: Grader guidance enforces a 1-page limit and single side-by-side comparison format that contradicts the prompt's 'For each school, create a PDF report (no more than 10 pages)' instruction
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement asks for a PDF report of no more than 10 pages for each school, so five separate per-school reports of up to 10 pages each meet the page-length and side-by-side items as fully as one combined 1-page comparison.
- other finding, major, not in findings.json: Rubric requires a 1-page deliverable, but the prompt allows up to 10 pages per report
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement asks for a PDF report of no more than 10 pages for each school, so five separate per-school reports of up to 10 pages each meet the page-length and side-by-side items as fully as one combined 1-page comparison.
- other finding, major, not in findings.json: Prompt asks for one report per school, but the rubric and GT expect one combined side-by-side file
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement asks for a PDF report of no more than 10 pages for each school, so five separate per-school reports of up to 10 pages each meet the page-length and side-by-side items as fully as one combined 1-page comparison.
- other finding, major, not in findings.json: Grader rewards a one-page comparison rather than the requested school reports
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement asks for a PDF report of no more than 10 pages for each school, so five separate per-school reports of up to 10 pages each meet the page-length and side-by-side items as fully as one combined 1-page comparison.
- other finding, major, not in findings.json: Core requirements to list nearby single-family homes for sale under $1,250,000 and school district details are ungraded and absent from ground truth
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement also asks for nearby single-family homes for sale under $1,250,000, the percentage of gifted students and the average teacher salary, which the expert deliverable and rubric leave out, so credit an agent that supplies these with stated sources as doing work the expert did not do.
- other finding, major, not in findings.json: Required home-search deliverables have no substantive grading coverage
  - Change: graderGuidance: added one sentence to the opening paragraph: The statement also asks for nearby single-family homes for sale under $1,250,000, the percentage of gifted students and the average teacher salary, which the expert deliverable and rubric leave out, so credit an agent that supplies these with stated sources as doing work the expert did not do.
- other finding, major, not in findings.json: Required home listings are not in the GT and not graded; the scoring scope doesn't match the prompt
  - Change: graderGuidance: added two sentences to the opening paragraph: The statement also asks for nearby single-family homes for sale under $1,250,000, the percentage of gifted students and the average teacher salary, which the expert deliverable and rubric leave out, so credit an agent that supplies these with stated sources as doing work the expert did not do. Where the agent takes its school data from another reputable source instead of Niche.com, credit that source's equivalent grades, rankings and source citation in place of the Niche.com items.
- other finding, major, not in findings.json: Rubric makes an example research source effectively mandatory
  - Change: graderGuidance: added one sentence to the opening paragraph: Where the agent takes its school data from another reputable source instead of Niche.com, credit that source's equivalent grades, rankings and source citation in place of the Niche.com items.
- other finding, minor, not in findings.json: Logo requirement is graded but never stated
  - Change: problemStatement: added one sentence before the Desktop line: "You work for Mort Realty, so brand the reports with the Mort Realty logo provided in your Desktop folder."
- other finding, major, not in findings.json: Grader guidance allocates 26 out of 82 points (31.7%) to undisclosed requirements (Mort Realty logo, official school websites, Diversity grades, and featured rankings)
  - Change: problemStatement: added the Mort Realty logo sentence ("You work for Mort Realty, so brand the reports with the Mort Realty logo provided in your Desktop folder."); graderGuidance: added the source-equivalence sentence: Where the agent takes its school data from another reputable source instead of Niche.com, credit that source's equivalent grades, rankings and source citation in place of the Niche.com items. Website, Diversity and featured-ranking items stay as expert checklist items under the pairwise comparison.

## Confirmed findings not fixed

- [F1](../findings.json): Graded values depend on live Niche.com data that is blocked and changes over time
  - Reason: infra
