# Changes: GDPval 6074bba3-7e3a-4b1c-b8c6-a15bb6695c3b

Fix summary (from the fix record):

No change. The comparable-sales and active-listing attachments the prompt promises were never part of the public GDPval task, the GT's addresses are scrubbed, and the named listing sites are blocked, so there is no faithful data to supply and dropping the comps would gut the rubric. Full pass: grader guidance gained a task-specific note (template section numbering accepted by name, distance/recency penalties tied to what the prompt states, comp-derived price statistics count as references, subject size/lease may be stated as not provided, scrubbed expert PDF quirks ignored).

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Rubric section numbers contradict the template the rubric also requires the agent to follow
  - Change: graderGuidance note: the template's 4-8 numbering meets the rubric's section items by name and counts as consistent with the template.
- other finding, major, not in findings.json: Contradiction between NEW CMA template.docx / problem.py and grader_guidance / GT on section numbering (4–6 vs 6–8) and required graphs
  - Change: Same graderGuidance note as another finding (not listed) (section numbering; the template's graph sections are accepted).
- other finding, major, not in findings.json: Grader section numbering conflicts with the required CMA template
  - Change: Same graderGuidance note as another finding (not listed).
- other finding, major, not in findings.json: Grader imposes undisclosed mandatory sold-comparable eligibility rules
  - Change: graderGuidance note: distance and recency penalties apply only to comps clearly outside the Adairsville submarket or clearly older than 12 months before the report date.
- other finding, major, not in findings.json: Undisclosed constraints in grader_guidance penalizing sold comps not within 1 to 3 miles and unprompted comp citations in template Section 8
  - Change: Same graderGuidance note as another finding (not listed), plus comp-derived price statistics in the pricing section count as referencing the comps.
- other finding, major, not in findings.json: The 'past 6–12 months' recency check is relative to an undefined date, and the GT data is over a year old
  - Change: graderGuidance note: the recency window is measured back from the report's own date.
- other finding, minor, not in findings.json: The statement asks for subject size and lease/occupancy details that no source provides, and the rubric then ignores them
  - Change: graderGuidance note: the subject's size and lease/occupancy are not in the materials, so stating them as not provided is acceptable.
- other finding, minor, not in findings.json: Scrubbed GT comps are inconsistent: one listing appears twice, ZIP codes point outside Adairsville, and chart labels show different addresses
  - Change: graderGuidance note: the grader ignores the scrubbed expert PDF's mismatched ZIPs, repeated listings and chart labels. The GT PDF itself is not rebuilt.

## Confirmed findings not fixed

- [F2](../findings.json): Comps and active listings are described as 'attached', but only the blank template is provided, and the agent can't reliably reach live listing sites
  - Reason: cannot-fix-safely: the promised comps/listings files do not exist in the source task and cannot be rebuilt faithfully (GT PDF addresses are scrubbed); adding invented data or removing the comp requirements would change the task beyond the defect
- [F1](../findings.json): Comparable sales and active listing reference files marked '(attached)' in prompt are missing from environment, third-party listing sites are blocked, and subject/comp addresses are scrubbed
  - Reason: duplicate-of:F2
- [F3](../findings.json): Promised comparable-sales and active-listing attachments are missing
  - Reason: duplicate-of:F2
