# Changes: GDPval a1963a68-1bea-4bb1-b7e0-145c92a57449

Fix summary (from the fix record):

Grader guidance note: the anonymised names (SuperK-Taxi, 'another competitor') may be satisfied by the real dominant competitor's name and by cited public data of the real brand behind SuperK-Taxi.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Anonymisation left the placeholder 'another competitor' inside rubric criteria
  - Change: graderGuidance: task note after the scoring paragraph saying 'another competitor' stands for the dominant Korean ride-hailing app and naming it by its real name satisfies those items. Rubric items unchanged. Not regraded locally (AI judge).
- other finding, major, not in findings.json: Incomplete anonymization of Uber Taxi (UT) Korea to 'SuperK-Taxi (SuperK-T)' creates impossible citation and ecosystem requirements in the rubric
  - Change: Same task note: cited public figures, service lines and rebranding facts of the real brand behind SuperK-Taxi count for the SuperK-Taxi fee-comparison, adjacent-service and rebranding items.
- other finding, major, not in findings.json: Anonymised company ('SuperK-Taxi') and unnamed rival make the required public-data research and cited competitor comparisons impossible to source honestly
  - Change: Same task note: such citations are not to be treated as fabrication or inconsistent terminology.
