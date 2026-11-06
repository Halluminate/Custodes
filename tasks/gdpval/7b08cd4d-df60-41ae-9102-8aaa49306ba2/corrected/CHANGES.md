# Changes: GDPval 7b08cd4d-df60-41ae-9102-8aaa49306ba2

Fix summary (from the fix record):

The rubric now accepts the expert's per-country withholding layout, the prompt's category labels and either placement of the unlabelled petty cash and fee lines, fixes the line-item typos, and checks the required as-of header.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: graderGuidance: the rubric items the expert workbook could not meet are reworded (per-stop or per-country withholding and net revenue, 'Hotel & Restaurants' label, Band and Crew label), so the ground truth no longer loses points against its own checklist. Not re-graded locally (GDPval pairwise AI grader).
- other finding, major, not in findings.json: The ground truth grades low under the guidance test (a stand-in for the production AI grader)
  - Change: Same graderGuidance rewording as exploit-probe-0.
- other finding, major, not in findings.json: Grader guidance mandates per-show withholding tax and net revenue calculations that contradict both the ground-truth workbook and the reference file structure
  - Change: graderGuidance: '[+2] For each tour stop, Withholding Amount ...' -> '[+2] Withholding Amount (USD), shown per tour stop or per country, equals the country’s withholding rate multiplied by the matching Combined Gross (USD).' and '[+2] For each tour stop, Net Revenue ...' -> '[+2] Net Revenue (USD), shown per tour stop or as a total, equals the matching Combined Gross (USD) minus the Withholding Amount (USD).' (expert computes withholding by country, E17:E20, and one Total Net Revenue, row 23).
- other finding, major, not in findings.json: The rubric requires a withholding and net-revenue figure for each tour stop, but the expert ground truth only calculates withholding by country
  - Change: Same per-stop/per-country withholding and net revenue rewording as another finding (not listed).
- other finding, major, not in findings.json: Grader guidance requires undisclosed category and line-item label changes that diverge from the prompt and reference workbook
  - Change: graderGuidance: Band and Crew item accepts 'Band and Crew' or 'Band and Crew (Fees & Per Diem)'; Hotel item now 'Hotel & Restaurants (singular or plural wording is fine)'; 'Transfer cards: 2,976' -> 'Car Service (transfer cars): 2,976'; 'Other: 1,679' -> 'Fees (other): 1,679', matching the reference file's Car Service and Fees lines.
- other finding, major, not in findings.json: Rubric requires exact category labels that differ from the labels the prompt asks for
  - Change: Same Band and Crew / Hotel & Restaurants label rewording as another finding (not listed).
- other finding, minor, not in findings.json: Typos and stray wording in rubric items
  - Change: graderGuidance: 'Other Tour Costs, Travel Production Company Total' -> 'Other Tour Costs, Production Company Total'; 'Transfer cards' -> 'Car Service (transfer cars)'; 'expenses as- London' -> 'expenses as - London'.
- other finding, major, not in findings.json: The rubric hardcodes one way of splitting the source's single 'Other Costs' bucket into the prompt's 'Other Tour Costs' and 'Other Travel Costs', and nothing in the materials states that split
  - Change: graderGuidance: one sentence before the formatting item accepts Petty Cash, Fees and the Tour Manager's Other line under either Other Tour Costs or Other Travel Costs, judging the two category totals by the agent's allocation as long as together they match the expert's 499,548 USD.
- other finding, major, not in findings.json: Graded travel-cost allocation is not supported by the source descriptions
  - Change: Same allocation sentence as another finding (not listed), plus the Car Service / Fees relabelling from another finding (not listed).
- other finding, minor, not in findings.json: Explicit prompt requirement to include 'As of 12/31/2024' in the header is omitted from grader guidance
  - Change: graderGuidance: added '[+1] The header shows the as-of date 12/31/2024 (12/31/24 is equivalent).' after the currency formatting item (expert G2 'As of 12/31/24' meets it).
