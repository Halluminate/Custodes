# Custodes: planted bugs

Every planted bug of Custodes, the QA benchmark from the post
[Custodes: Who annotates the annotators?](https://halluminate.ai/blog/qa-benchmark).

We start from 40 internal long-horizon finance RL tasks. For each task, bucket, and tier we write three
bugs, which gives 40 tasks x 5 buckets x 3 tiers x 3 bugs = 1,800 single-bug copies.

- 200 of them (one per bucket and task, at random) form the single-bug set.
- The 40 all-bugs copies carry all compatible bugs of a task at once, 1,416 bugs in total.

`planted_bugs.csv` has one row per bug:

| column | meaning |
|---|---|
| `task` | task number, 1 to 40 (task names are not public) |
| `bucket` | Task Spec, Reward, Environment & Infra, Verification, or Style |
| `tier` | Obvious, Subtle, or Near-impossible |
| `variant` | A, B, or C (three bugs per task, bucket, and tier) |
| `qa_issue_type` | one of the 28 QA issue types (Figure 3 of the post) |
| `description` | one line on how the bug was planted in that task |
| `in_single_bug_set` | 1 if the bug is one of the 200 single-bug copies |
| `in_all_bugs_set` | 1 if the bug is part of its task's all-bugs copy |

The tasks themselves are internal and not released.
