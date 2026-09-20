# Allocator v6 profiling results

This folder contains four items:

- `results.csv`: all 120 measured executions in one document
- `report-summary.md`: this analysis
- `environment.txt`: machine, OS, compiler, build, and version information
- `run-logs/`: every measured stdout, stderr, timing, and exit-status log

The results cover four workloads at short, medium, and long scales. Each batch
contains five regular-`new` and five overloaded-`new` executions. All 120
executions exited successfully, and regular/overloaded checksums matched.

## Quick analysis

Performance effect is `(regular mean - overloaded mean) / regular mean`. A
positive percentage means overloaded `new` was faster.

- Matrix: overloaded was 2.38% faster short, 2.32% faster medium, and 2.33%
  faster long.
- Uniform nodes: overloaded was 3.06% faster short, 3.06% faster medium, and
  3.05% faster long.
- Nested memory stress: overloaded was 7.00% slower short, 6.33% slower
  medium, and 5.86% slower long.
- Linked list: overloaded was 0.26% slower short, 0.25% slower medium, and
  0.20% slower long. This is close to neutral in practical terms.

V6 therefore showed a small, repeatable improvement for matrix and uniform-node
workloads, a repeatable regression for nested memory stress, and little change
for linked lists.

## Test environment

- Apple M3 Max, 16 cores (12 performance and 4 efficiency)
- 48 GB unified memory
- macOS 26.5.2, build 25F84
- Apple clang 17.0.0, Release build
- Allocator tag v6.0.0, commit
  `f68dadcfc67e8764cbdbcf2768390284d43e2f32`
- Project commit `12617e0f943a7b68d8334aa5477dfa403a75ca21`

Five regular and five overloaded processes ran concurrently in each batch.
Short executions lasted 3-5 minutes, medium executions 2-3 hours, and long
executions more than 6 hours. Peak resident memory is unavailable because the
macOS portable timing mode recorded elapsed, user, and system time only.

Do not directly compare v6 absolute elapsed times with v7 because the versions
ran on different machines with independently calibrated workloads.
