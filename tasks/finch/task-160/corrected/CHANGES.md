# Changes: FINCH task-160

Fix summary (from the fix record):

The prompt now asks for a new Excel file instead of a non-existent 'the Excel file'. The guidance tells the judge not to require the reference's helper column L and check cells, which are not in the PDF.

Changed files (in this folder):

- prompt.md
- grader_guidance.md

## Fixed

- other finding, minor, not in findings.json: The task asks for 'the Excel file', but no Excel file is provided and no output name is given. The statement also has a typo ('pdfinto').
  - Change: Prompt sentence "Transcribe the content from the pdfinto the Excel file." -> "Transcribe the content from the PDF into a new Excel file." (typo fixed, no phantom workbook).
- other finding, major, not in findings.json: The reference workbook has a helper column and check row that are not in the PDF, so the grader may penalize a faithful transcription
  - Change: graderGuidance: added one sentence after the opening paragraph: the reference's helper column L (L11:L25) and check cells F51/H51 are working aids not in the PDF and must not be required or counted against the output. The GT is unchanged because H25 is computed from L25.
