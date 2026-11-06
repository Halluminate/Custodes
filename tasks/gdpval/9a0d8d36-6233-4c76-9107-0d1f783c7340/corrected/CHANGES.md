# Changes: GDPval 9a0d8d36-6233-4c76-9107-0d1f783c7340

Fix summary (from the fix record):

Answer-key deck: slide 4 now states the NSO ordinary income as the spread between strike and fair market value at exercise, and slide 7 shows the NSO cost basis as $75,000. One guidance sentence tells the judge not to credit the expert deck with the rubric items it misses.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_Incentive and Non Qualified Stock Options.pptx

## Fixed

- other finding, major, not in findings.json: Answer-key deck states the NSO ordinary-income rule wrongly and mislabels the NSO cost basis
  - Change: gt_Incentive and Non Qualified Stock Options.pptx (XML text edit, all else byte-identical): slide 4 'The spread between the strike price and the sales price is taxed as ordinary income' -> 'the strike price and the fair market value at exercise'; slide 7 'Cost Basis at Exercise = $20,000' -> '$75,000' (the basis its own $25,000 gain uses).
- other finding, major, not in findings.json: Expert reference fails many of the rubric's own items, so the pairwise grade is too lenient and inconsistent with the rubric
  - Change: grader guidance: added one sentence after the scoring line: the expert deck does not compute NSO payroll taxes, state the 2-year/1-year ISO holding periods, say it is educational/not tax advice, say the options are not yet vested, or put the two net proceeds side by side, so the judge does not credit it with those rubric items. Its NSO definition error is fixed in the deck (see another finding (not listed)).
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: The unstable ground-truth grades trace to the expert deck failing rubric items it is compared on; addressed by the deck corrections (another finding (not listed)) and the added guidance sentence (another finding (not listed)). Not re-probed locally.
