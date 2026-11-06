# Changes: GDPval 5ad0c554-a7a2-48cd-b41a-ebc1bff4a9de

Fix summary (from the fix record):

The prompt says reference files are on the Desktop, but the '132 Things' PDF was never staged and the URL is blocked in runs. The PDF is now supplied as a data file under its original name. Full pass: the five per-section rubric lines no longer require citing the '132 Things' document by title or item number inside the client brochure (the prompt never asks for it and the expert brochure has none); they still require an action drawn from the reference.

Changed files (in this folder):

- grader_guidance.md
- inputs/132-Things-REALTORS-Do-For-Buyers.pdf (new file)

## Fixed

- [F1](../findings.json) (Environment & Infra): Prompt states reference files are on Desktop, but the reference PDF is only available via external URL
  - Change: Added the reference PDF as a data file: files/data/132-Things-REALTORS-Do-For-Buyers.pdf (4 pages, the 132-item list, downloaded 2026-11-05 from the URL in the prompt, HTTP 200, application/pdf). It is staged on the Desktop under the same name, so the prompt's 'Any reference files mentioned above are in your Desktop folder' becomes true and agents no longer need the blocked URL. NOTE: data/ was empty, so this is a NEW data file, not a replacement. Applying it needs the dataFiles editor patch (an upload alone does not reach runs). No prompt change.
- [F3](../findings.json) (Environment & Infra): The reference PDF is not on the Desktop, but the statement says reference files are there
  - Change: Same new data file: the 132 Things PDF is staged on the Desktop.
- [F2](../findings.json) (Environment & Infra): Required reference PDF is not staged on the Desktop
  - Change: Same new data file: the 132 Things PDF is staged on the Desktop.
- other finding, critical, not in findings.json: bash (curl through agent-egress squid proxy): Egress squid proxy denies the task-required BubbleInfo source PDF with HTTP 403 ERR_ACCESS_DENIED on every route, so the agent falls back to reconstructing content from memory
  - Change: The proxy 403 itself is harness behaviour, but the task caused the need for it: with the PDF staged on the Desktop the agent no longer has to fetch it.
- other finding, major, not in findings.json: Grader guidance awards 5 points for explicit reference attribution that neither the prompt nor the ground truth includes
  - Change: grader_guidance.md: in the five '[+1] In the <section> section, identifies at least one specific buyer-agent action...' lines, 'and explicitly attributes it to the reference (by document title or item number)' became 'drawn from the reference (an explicit citation by document title or item number is welcome but not required)'. No other line changed, no prompt change.
- other finding, major, not in findings.json: Grading requires citing the source and an exact 2-page length, but the prompt asks for neither
  - Change: Same guidance change for the attribution part. The two-page line is kept: the prompt asks for a double-sided brochure.
