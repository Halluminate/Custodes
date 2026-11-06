# QA of public RL tasks: External Benchmarks

This repository holds 536 public benchmark tasks that we ran through our QA pipeline. For each task it has
the task as we QA'd it, the corrected files where we changed something, and the confirmed QA findings.

| Benchmark | Official source | Tasks | Tasks with corrected files | Confirmed findings (pipeline) | Findings fixed | Single-pass findings |
|---|---|---:|---:|---:|---:|---:|
| SpreadsheetBench 2 | [KAKA22/SpreadsheetBench-v2](https://huggingface.co/datasets/KAKA22/SpreadsheetBench-v2) | 321 | 251 | 716 (168 tasks) | 651 | 134 |
| FINCH | [FinWorkBench/Finch](https://huggingface.co/datasets/FinWorkBench/Finch) | 172 | 136 | 129 (42 tasks) | 128 | 24 |
| GDPval (gold subset, finance occupations) | [openai/gdpval](https://huggingface.co/datasets/openai/gdpval) | 40 | 35 | 53 (13 tasks) | 40 | 17 |
| DAYJOB (finance) | [surgeai/DAYJOB-finance](https://huggingface.co/datasets/surgeai/DAYJOB-finance) | 3 | 3 | 0 | 0 | 0 |
| Total | | 536 | 425 | 898 (223 tasks) | 819 | 175 |

## What "original" means

`original/` is the task exactly as our QA pipeline saw it: the public task ported to our agent harness, with
prompt, grading and reference files set up to follow each benchmark's official run and grading setup. It is not
a byte copy of the public release. Known differences from the public release:

- SpreadsheetBench 2: the official agent prompt template is the prompt (tool names adapted to our harness).
  Grading is a deterministic cell check (297 tasks) or a chart checklist (24 tasks), as in the official
  scorer. An untouched copy of the input (`untouched_input_*.xlsx`) sits in `reference/` because the cell check
  compares against it. Some reference workbooks had defined names removed (a platform upload limit),
  with cell values and formulas unchanged.
- FINCH: the official judge prompt is the grader guidance. The prompt footer names the output folder. For the
  text-answer tasks the public reference text is stored as `gt_answer.txt`.
- GDPval: the grader guidance asks for the official pairwise comparison with the expert deliverable, plus the
  public rubric. Tasks with no public deliverable have a `reference_note.txt` instead.
- DAYJOB: the official preamble is in the prompt and the official judge template, with every criterion, is the
  grader guidance. `reference/reference_note.txt` replaces the absent public deliverable.

For the raw public files, use the official sources above.

## The 5 buckets

Each confirmed finding has exactly one bucket, the one that best describes what is broken in the task:

- **Environment & Infra**: the inputs the agent works from are broken, missing, stale or inconsistent (data
  files, seeded workbook values, missing referenced files, file names that leak the answer).
- **Task Spec**: the instructions are wrong, contradictory, ambiguous or underspecified (prompt text, requested
  outputs, conventions the grader enforces but the prompt never states, prompt contradicting the inputs).
- **Verification**: the expected answer itself is wrong (answer-key, golden or reference values, formulas or
  text that are incorrect, incomplete or stale).
- **Reward**: the grading mechanism is wrong even if the answer key is right (verifier ranges, cells, mode,
  weights or thresholds, rubric items that cannot be met or credit the wrong thing, unstable grading).
- **Style**: presentation only (formatting, fonts, colours, number formats, chart cosmetics, layout, labels).

Confirmed pipeline findings per bucket:

| Bucket | SpreadsheetBench 2 | FINCH | GDPval | Total |
|---|---:|---:|---:|---:|
| Verification | 364 | 97 | 15 | 476 |
| Reward | 220 | 3 | 10 | 233 |
| Task Spec | 97 | 10 | 10 | 117 |
| Environment & Infra | 24 | 15 | 18 | 57 |
| Style | 11 | 4 | 0 | 15 |

## Layout

```
tasks/<benchmark>/<task>/
  original/
    prompt.md            task prompt
    grader_guidance.md   grader instructions (judge prompt, rubric or check description)
    grading.json         grader mode, verifier functions and parameters, AI-grader settings
    inputs/              files given to the agent
    reference/           answer key / golden / expert deliverable, as used by the grader
  corrected/             only present if we changed the task; only the changed files
    CHANGES.md           what was changed and why, linked to findings.json
  findings.json          confirmed findings (pipeline): id, title, bucket, severity, category,
                         evidence, confirmation (why the finding was confirmed), fixed, fix
single_pass/<benchmark>/<task>/findings.json   confirmed findings from a single-pass LLM review baseline
single_pass/summary.csv                        one row per single-pass finding
findings/summary.csv                           one row per confirmed pipeline finding
scores/before_after.csv                        DeepSeek V4.1 Flash mean score per corrected task, before and after
MISSING.md                                     files that are not in this repository
```

Task names: SpreadsheetBench 2 tasks use the public task id (for example `financial-model-01_01`,
`debugging-03_04`, `template-06_11`, `visualization-task-126`), FINCH tasks the public task number
(`task-011`), GDPval tasks the public task id, DAYJOB tasks the public task id.

## Findings

Findings come from our multi-check QA pipeline, run on one 3-attempt DeepSeek V4.1 Flash rollout per task.
Only critical findings that a separate checker confirmed as real are listed (898), each with the finding text,
the evidence and the checker's confirmation. Not listed: 90 confirmed findings from the tool-runtime and exploit
checks, which are about our harness and tools, and 10 other confirmed findings that were left out of the bucket
classification.
`fixed` is true when the applied correction lists that finding as fixed. Some corrections also fixed major or
minor findings that are not listed here; `CHANGES.md` marks those as "another finding (not listed)".

Identifiers internal to our platform (problem ids, run ids, internal paths) are replaced by `<id>` or removed in the
finding and change texts. References to other findings in the same task are rewritten to their `F<n>` id.

`single_pass/` holds the 175 confirmed critical findings of a single-pass LLM review baseline over the same tasks.
These were not used to choose the corrections, so they have no `fixed` field.

## Scores

`scores/before_after.csv` gives, for the 425 corrected tasks, the mean score of DeepSeek V4.1 Flash over 3 attempts
before the fixes and over a new 3-attempt run after the fixes. One GDPval after-run failed and has no score.

| Benchmark | Corrected tasks | Mean before | Mean after |
|---|---:|---:|---:|
| SpreadsheetBench 2 | 251 | 0.212 | 0.463 |
| FINCH | 136 | 0.591 | 0.700 |
| GDPval | 35 (34 with an after score) | 0.717 | 0.742 |
| DAYJOB | 3 | 0.551 | 0.576 |

## Omitted files

Files over 20 MB are not included (see `MISSING.md`): the input `<n>_src_5.csv` (23.6 MB) of FINCH tasks
`task-017`, `task-018` and `task-073`.
