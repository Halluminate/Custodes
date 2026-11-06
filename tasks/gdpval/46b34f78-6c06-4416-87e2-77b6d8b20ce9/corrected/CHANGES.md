# Changes: GDPval 46b34f78-6c06-4416-87e2-77b6d8b20ce9

Fix summary (from the fix record):

The only input file was an unreadable .docx (broken relationship XML, sanitized link targets, prefixed package XML); it is repaired so Word tools open it, with the original link targets restored from the visible link text. The expert memo's HY note now says 7% (its table's total), and the guidance lists the rubric items the expert misses so the pairwise judge does not credit it with them.

Changed files (in this folder):

- grader_guidance.md
- reference/gt_Energy Trading and Sales Strategy.docx
- inputs/Research Material.docx

## Fixed

- [F2](../findings.json) (Environment & Infra): Corrupted XML in staged reference file 'Research Material.docx' causes LibreOffice and python-docx to crash, and replaces all hyperlink targets with 'https://example.invalid/_external'
  - Change: data/Research Material.docx repaired: word/_rels/document.xml.rels had nine hyperlink <Relationship> elements missing their closing '/>' and pointing at https://example.invalid/_external; each is now closed and points at the URL its link text shows (eia.gov, bloomberg.com/markets/commodities, ... esgtoday.com). [Content_Types].xml and _rels/.rels were also rewritten from 'ns0:'-prefixed XML to the standard default namespace, which LibreOffice needs to open the package. document.xml, styles and fonts are byte-identical. The file now opens in python-docx and converts in LibreOffice.
- [F1](../findings.json) (Environment & Infra): The only input file, Research Material.docx, is corrupt: LibreOffice and python-docx both fail to open it
  - Change: data/Research Material.docx repaired: word/_rels/document.xml.rels had nine hyperlink <Relationship> elements missing their closing '/>' and pointing at https://example.invalid/_external; each is now closed and points at the URL its link text shows (eia.gov, bloomberg.com/markets/commodities, ... esgtoday.com). [Content_Types].xml and _rels/.rels were also rewritten from 'ns0:'-prefixed XML to the standard default namespace, which LibreOffice needs to open the package. document.xml, styles and fonts are byte-identical. The file now opens in python-docx and converts in LibreOffice.
- other finding, critical, not in findings.json: Required research reference is a corrupt Word document with invalid hyperlink targets
  - Change: data/Research Material.docx repaired: word/_rels/document.xml.rels had nine hyperlink <Relationship> elements missing their closing '/>' and pointing at https://example.invalid/_external; each is now closed and points at the URL its link text shows (eia.gov, bloomberg.com/markets/commodities, ... esgtoday.com). [Content_Types].xml and _rels/.rels were also rewritten from 'ns0:'-prefixed XML to the standard default namespace, which LibreOffice needs to open the package. document.xml, styles and fonts are byte-identical. The file now opens in python-docx and converts in LibreOffice.
- other finding, major, not in findings.json: In the GT sample allocation, the HY share stated in the notes does not match the table
  - Change: gt_Energy Trading and Sales Strategy.docx (word/document.xml text edit, built on the original expert file, all else byte-identical): Note 2 'The sample allocation’s 14% HY share' -> '7% HY share', the total of its own table (HY LNG Exporters 4% + HY Other Energy 3%). The missing dollar figure is covered by the guidance sentence (see another finding (not listed)).
- other finding, major, not in findings.json: Grader guidance includes 28 points (out of 75) of undisclosed constraints not stated in the task prompt or reference file and missing from the ground-truth deliverable itself
  - Change: grader_guidance.md: added one sentence after the scoring line listing the rubric items the expert memo misses (HY allocation in dollars, a specific bond by coupon/maturity or ISIN/CUSIP, a numeric risk parameter, dated citations, a current oil issuer), so the pairwise judge does not credit the expert with them. The official rubric items themselves are unchanged.
- other finding, major, not in findings.json: The GT's issuer analysis contains outdated or wrong facts and leaves out rubric-required bond details
  - Change: Same added guidance sentence: the expert memo is not credited with the bond-identification, risk-parameter and dated-citation items it misses, and the judge is told that Pioneer Natural Resources was acquired by ExxonMobil in May 2024. The expert's issuer analysis cannot be rewritten without inventing content.
- other finding, major, not in findings.json: The ground truth gets different grades from the guidance test (a stand-in for the production AI grader)
  - Change: Same expert-gaps sentence as another finding (not listed) plus the 7% HY correction (another finding (not listed)), so the pairwise grader has a stable view of where the expert falls short. Not re-graded locally (GDPval pairwise AI grader).
