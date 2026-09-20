# Allocator v7 profiling results

This folder contains four items:

- `results.csv`: all 120 measured executions in one document
- `report-summary.md`: this analysis
- `environment.txt`: machine, OS, compiler, build, and version information
- `run-logs/`: every measured stdout, stderr, timing, exit-status, and metadata
  log

The results cover four workloads at short, medium, and long scales. Each batch
contains five regular-`new` and five overloaded-`new` executions. All 120
executions exited successfully, and regular/overloaded checksums matched.

## Quick analysis

Performance effect is `(regular mean - overloaded mean) / regular mean`. A
negative percentage means overloaded `new` was slower.

- Matrix: overloaded was 10.74% slower short, 8.78% slower medium, and 9.65%
  slower long.
- Uniform nodes: overloaded was 9.64% slower short, 9.66% slower medium, and
  9.73% slower long.
- Nested memory stress: overloaded was 4.83% slower short, 4.43% slower
  medium, and 4.18% slower long.
- Linked list: overloaded was 13.05% slower short, 12.15% slower medium, and
  11.02% slower long.

V7 overloaded allocation was slower than regular `new` in all 12 measured
batches. Averaged equally across the three scales, its peak resident memory was
approximately 4.01% higher for matrix, 3.29% higher for nodes, 27.87% higher
for memory stress, and 155.38% higher for linked lists.

## Test environment

- AMD Ryzen 9 7900X, 12 physical cores and 24 logical processors
- 32 GB DDR5-5200; WSL configured for 24 GB RAM and 8 GB swap
- Windows 11 Home 10.0.26200 with WSL2 and Ubuntu 24.04 LTS
- GCC 13.3.0 and libstdc++, Release build
- Allocator tag v7.0.0, commit
  `d3c2ee7437cdb768b1f69de76287d33c539d6973`
- Project commit `12617e0f943a7b68d8334aa5477dfa403a75ca21`

Five regular and five overloaded processes ran concurrently in each batch.
Short executions lasted 3-5 minutes, medium executions 2-3 hours, and long
executions more than 6 hours.

Do not directly compare v7 absolute elapsed times with v6 because the versions
ran on different machines with independently calibrated workloads.
