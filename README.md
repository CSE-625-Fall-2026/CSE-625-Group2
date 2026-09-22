# CSE-625 Group 2 - Assignment 1

LaTeX source files, profiling test scripts / raw data, and v8 allocator improvement code.


## Repository Layout

```
assignment_1/
  main.tex            # report root
  bibliography.bib    # biblatex/biber sources
  sections/           # \input section files
  figures/            # chart images for the report
  scripts/            # profiling scripts
  slides/             # Beamer slideshow
    main.tex          #   presentation root
    sections/         #   one file per topic
    figures/          #   chart images for the slides
  TestingResults/     # raw measurement data & profiling scripts
UsingMatrixClass/     # submodule: workload programs, v8 improvement code, CMake build
```

## Publishing a PDF

PDFs are produced by the Github action
[.github/workflows/build-latex.yml](.github/workflows/build-latex.yml) which
compiles the report and the slideshow on every push and pull request. Compiled PDFs are uploaded together as a release.

To publish a submission, tag the commit and push the tag. The same two PDFs
are then attached to a GitHub Release as `<tag>-report.pdf` and
`<tag>-slides.pdf`:

### Example: 
```
git tag v1.0.0
git push origin v1.0.0
```

## Results:
### Table Inventory

| Table ID | Environment | Parameters |
| --- | --- | --- |
| v8.0.0\|Matrix\|1 | Machine ID: mohamed-m3max-v8-full \| Averages | arg1=360 |
| v7.0.0\|Matrix\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on AMD Ryzen 9 7900X 12-Core Processor \| 32GB \| WSL Ubuntu 24.04 LTS \| Averages | — |
| v7.0.0\|Uniform Nodes\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on AMD Ryzen 9 7900X 12-Core Processor \| 32GB \| WSL Ubuntu 24.04 LTS \| Averages | — |
| v7.0.0\|Memory Stress\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on AMD Ryzen 9 7900X 12-Core Processor \| 32GB \| WSL Ubuntu 24.04 LTS \| Averages | — |
| v7.0.0\|Linked List\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on AMD Ryzen 9 7900X 12-Core Processor \| 32GB \| WSL Ubuntu 24.04 LTS \| Averages | — |
| v7.0.0\|Matrix\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v6.0.0\|Matrix\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on 12 core Apple M3 Max \| Not Collected \| 48GB \| MacOS 26.5.2, build 25F84 \| Averages | — |
| v6.0.0\|Uniform Nodes\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on 12 core Apple M3 Max \| Not Collected \| 48GB \| MacOS 26.5.2, build 25F84 \| Averages | — |
| v6.0.0\|Memory Stress\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on 12 core Apple M3 Max \| Not Collected \| 48GB \| MacOS 26.5.2, build 25F84 \| Averages | — |
| v6.0.0\|Linked List\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on 12 core Apple M3 Max \| Not Collected \| 48GB \| MacOS 26.5.2, build 25F84 \| Averages | — |
| v6.0.0\|Matrix\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v5.0.0\|Matrix\|1 | Averages \| Using an Intel i7-11800H 8 core 16 thread @ 2.3 GHz up to 4.6 GHz | — |
| v5.0.0\|Uniform Nodes\|1 | AMD Ryzen 7 7800X3D (Zen 4) \| Ubuntu 26.04 (WSL2), glibc, g++ 15.2.0 | Short (size 100, 35,000 passes); Medium (size 100, 1,335,000 passes); Long (size 100, 4,100,000 passes) |
| v5.0.0\|Uniform Nodes\|2 | MacBook Pro Apple M5 Pro (arm64) \| macOS 26.6.2, Apple Clang, 24 GB | Short (size 100, 35,000 passes); Medium (size 100, 1,335,000 passes); Long (size 100, 4,100,000 passes) |
| v5.0.0\|Memory Stress\|1 | Not specified | — |
| v5.0.0\|Linked List\|1 | Not specified | — |
| v5.0.0\|Matrix\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v5.0.0\|Uniform Nodes\|3 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v4.0.0\|Matrix\|1 | Not specified | — |
| v4.0.0\|Uniform Nodes\|1 | Assignee \| Jose Fuentes - Group 1 \| Ubuntu 26.04 (WSL2), glibc, g++ 15.2.0 \| AMD Ryzen 7 7800X3D (Zen 4) \| Averages | Short  (size 100, 35,000 passes); Medium  (size 100, 1,335,000 passes); Long  (size 100, 4,100,000 passes) |
| v4.0.0\|Uniform Nodes\|2 | Assignee \| Jose Fuentes - Group 1 \| macOS 26.6.2, Apple Clang, 24 GB \| MacBook Pro M5 Pro (arm64) \| Averages (mean of 5 runs) | Short (size 100, 35,000 passes); Medium (size 100, 1,335,000 passes); Long (size 100, 4,100,000 passes) |
| v4.0.0\|Memory Stress\|1 | Not specified | — |
| v4.0.0\|Linked List\|1 | Not specified | — |
| v4.0.0\|Matrix\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v4.0.0\|Uniform Nodes\|3 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v3.0.0\|Matrix\|1 | Thinkpad X13 Yoga Gen 1 \| 16 GB of RAM \| Using WSL (Windows Subsystem for Linux) \| 4-core, 8-thread mobile processor with a base clock of 1.8 GHz \| Averages | — |
| v3.0.0\|Uniform Nodes\|1 | Not specified | Short (225 x 225), 600 passes; Medium (800 x 800), 600 passes |
| v3.0.0\|Memory Stress\|1 | Not specified | Short (200 rounds); Medium (1000 rounds; longer duration ones not needed due to obvious gap where regular is linear, but overloaded appears not to be) |
| v3.0.0\|Linked List\|1 | Not specified | — |
| v3.0.0\|Matrix\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v2.0.0\|Matrix\|1 | Assignee: \| Jacob Nance - Team 2 \| Run on 4 consecutive 11th Gen Intel® Core™ i7-1165G7  processors \| 16GB Memory \| Ubuntu 24.04.3 LTS  OS \| Averages | Short = 275 \| Med = 900 \| Long = 1225 |
| v2.0.0\|Uniform Nodes\|1 | Assignee: \| Jacob Nance - Team 2 \| Run on 4 consecutive 11th Gen Intel® Core™ i7-1165G7  processors \| 16GB Memory \| Ubuntu 24.04.3 LTS  OS \| Averages | Arg1 \| Short = 285 \| Med = 900 \| Large = 1200; All = 600 \| Averages |
| v2.0.0\|Memory Stress\|1 | Assignee: \| Jacob Nance - Team 2 \| Run on 4 consecutive 11th Gen Intel® Core™ i7-1165G7  processors \| 16GB Memory \| Ubuntu 24.04.3 LTS  OS \| Averages | Short = 100 \| Med = 440 \| Long = 900 |
| v2.0.0\|Linked List\|1 | Assignee: \| Jacob Nance - Team 2 \| Run on 4 consecutive 11th Gen Intel® Core™ i7-1165G7  processors \| 16GB Memory \| Ubuntu 24.04.3 LTS  OS \| Averages | Short = 125000 \| Med = 580000 \| Long = 875000 |
| v2.0.0\|Matrix\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v1.0.0\|Matrix\|1 | Not specified | — |
| v1.0.0\|Uniform Nodes\|1 | Not specified | — |
| v1.0.0\|Memory Stress\|1 | Not specified | — |
| v1.0.0\|Linked List\|1 | Not specified | — |
| v1.0.0\|Matrix\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |

### Analysis Summary

| Table ID | Summary |
| --- | --- |
| v8.0.0\|Matrix\|1 | Matrix (environment 1): overloaded runtime changed -4.87%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.01301). |
| v7.0.0\|Matrix\|1 | Matrix (environment 1): overloaded runtime changed 9.73%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001226). |
| v7.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): overloaded runtime changed 4.48%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0007384). |
| v7.0.0\|Memory Stress\|1 | Memory Stress (environment 1): overloaded runtime changed 9.68%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0009381). |
| v7.0.0\|Linked List\|1 | Linked List (environment 1): overloaded runtime changed 12.08%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0007449). |
| v7.0.0\|Matrix\|2 | Matrix (environment 2): overloaded runtime changed 5.10%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001422). |
| v6.0.0\|Matrix\|1 | Matrix (environment 1): overloaded runtime changed -2.34%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0008068). |
| v6.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): overloaded runtime changed 6.40%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0007226). |
| v6.0.0\|Memory Stress\|1 | Memory Stress (environment 1): overloaded runtime changed -3.06%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0008024). |
| v6.0.0\|Linked List\|1 | Linked List (environment 1): overloaded runtime changed 0.24%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0004065). |
| v6.0.0\|Matrix\|2 | Matrix (environment 2): overloaded runtime changed 6.52%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001404). |
| v5.0.0\|Matrix\|1 | Matrix (environment 1): overloaded runtime changed 0.37%; did not improve. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.7255). |
| v5.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): insufficient paired runtime data. |
| v5.0.0\|Uniform Nodes\|2 | Uniform Nodes (environment 2): insufficient paired runtime data. |
| v5.0.0\|Memory Stress\|1 | Memory Stress (environment 1): insufficient paired runtime data. |
| v5.0.0\|Linked List\|1 | Linked List (environment 1): insufficient paired runtime data. |
| v5.0.0\|Matrix\|2 | Matrix (environment 2): overloaded runtime changed -6.44%; improved. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.4695). |
| v5.0.0\|Uniform Nodes\|3 | Uniform Nodes (environment 3): overloaded runtime changed 5.39%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001816). |
| v4.0.0\|Matrix\|1 | Matrix (environment 1): overloaded runtime changed -1.79%; improved. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.6398). |
| v4.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): insufficient paired runtime data. |
| v4.0.0\|Uniform Nodes\|2 | Uniform Nodes (environment 2): insufficient paired runtime data. |
| v4.0.0\|Memory Stress\|1 | Memory Stress (environment 1): insufficient paired runtime data. |
| v4.0.0\|Linked List\|1 | Linked List (environment 1): insufficient paired runtime data. |
| v4.0.0\|Matrix\|2 | Matrix (environment 2): overloaded runtime changed -0.80%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.02894). |
| v4.0.0\|Uniform Nodes\|3 | Uniform Nodes (environment 3): overloaded runtime changed 2.55%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.008073). |
| v3.0.0\|Matrix\|1 | Matrix (environment 1): insufficient paired runtime data. |
| v3.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): insufficient paired runtime data. |
| v3.0.0\|Memory Stress\|1 | Memory Stress (environment 1): insufficient paired runtime data. |
| v3.0.0\|Linked List\|1 | Linked List (environment 1): insufficient paired runtime data. |
| v3.0.0\|Matrix\|2 | Matrix (environment 2): overloaded runtime changed 0.66%; did not improve. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.2328). |
| v2.0.0\|Matrix\|1 | Matrix (environment 1): overloaded runtime changed -13.63%; improved. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.073). |
| v2.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): overloaded runtime changed -7.02%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.04021). |
| v2.0.0\|Memory Stress\|1 | Memory Stress (environment 1): overloaded runtime changed 2333.61%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0007268). |
| v2.0.0\|Linked List\|1 | Linked List (environment 1): overloaded runtime changed 32457.14%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0006808). |
| v2.0.0\|Matrix\|2 | Matrix (environment 2): overloaded runtime changed 3.81%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001308). |
| v1.0.0\|Matrix\|1 | Matrix (environment 1): insufficient paired runtime data. |
| v1.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): insufficient paired runtime data. |
| v1.0.0\|Memory Stress\|1 | Memory Stress (environment 1): insufficient paired runtime data. |
| v1.0.0\|Linked List\|1 | Linked List (environment 1): insufficient paired runtime data. |
| v1.0.0\|Matrix\|2 | Matrix (environment 2): overloaded runtime changed 22.58%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.01417). |


## Responses to README Questions

These are our answers to the seventeen questions at the end of the README.
They are grouped into four themes. The same answers appear in Section XIV of
the report, where they are typeset with full citations.

### Profiling and Measurement

**What do you notice as the profiling scale increases in each test case?**

The performance gap between the custom allocator and regular `new` stayed
roughly constant as scale increased. Peak memory barely changed between the
short, medium, and long tests. This suggests the scale parameter repeats the
same working set rather than enlarging it, which means the pool's memory
overhead stayed fixed. Minor page faults grew almost exactly in proportion to
elapsed time. Overall, the choice of test case mattered more than the scale.

**Why is a fixed random seed important for a fair comparison?**

It is important that all versions face the same seed to ensure fairness when
comparing performance. This ensures that no one version is doing any more or
less work than the others. A fixed seed also makes results reproducible.

**How could execution order affect measured results?**

Execution order matters because each test inherits the machine state left by
whatever ran before it. That state includes the operating system's page cache,
which already holds the executable and shared libraries after the first test
has loaded them, as well as the CPU's frequency and thermal state. A test
running second is therefore measured under different conditions than the same
test running first: whichever test runs first pays that cost and whichever
runs second gets it for free.

**Why should several runs and median times be used for profiling?**

Several runs and median times should be used for profiling to avoid the data
being skewed by outliers. This prevents an anomaly that slowed down one run
from affecting the profiling data too much.

**Which measurements should be collected in addition to elapsed time?**

Because the results are collected across multiple teams, the environment must
be recorded alongside the timing. This includes CPU model, core count,
operating system version, and compiler version. Additionally, each run records
CPU utilization and peak memory usage. Each run also records minor page
faults, which showed that regular `new` incurred many times more of them than
the overloaded version.

### Allocator Design and Workload Fit

**When could a known access pattern make an allocator heuristic effective?**

A heuristic is effective when the workload matches the assumption it encodes.
Knowing the pattern in advance lets you pick the heuristic that skips exactly
the work your workload would never need.

**Why might the system allocator outperform a custom allocator for small
nodes?**

Our linked-list test was the worst case for the custom allocator. It was
slower than regular `new` at every scale and had 2.55 times the peak memory.
Our matrix-based tests differed by only 3-28% in memory. The cause is that
per-allocation overhead is a fixed cost regardless of object size, so it
dominates when the objects are small.

**How does fragmentation affect allocation search time and memory use?**

Fragmentation means free memory exists but is split into pieces too small to
satisfy a request. This means an allocation can fail even when total free
space is sufficient [1]. Search time grows because there are more free-list
entries to examine.

**How do canaries and allocation metadata affect speed and memory use?**

In v7, `allocation_overhead` is 64 bytes per allocation: a 48-byte header, an
8-byte owner pointer, and two 4-byte canaries. For the 72-byte linked-list
node, header, alignment padding, and canaries bring the block to 144 bytes,
which the slab refill then rounds up to 192 bytes. Every allocation writes two
canaries and an owner pointer. Every deallocation reads and compares both
canaries before freeing. This operation is cheap but can be significant when
working with a small node.

**How should cache limits and size classes be selected for a workload?**

They should be chosen by measuring the workload's actual request sizes rather
than fixed in advance. Cache limits should be sized to each thread's working
set per class and capped by a total byte budget multiplied across all threads.

**When could an allocator optimized for one workload harm another workload?**

Optimizations usually assume some specific scenario, so if that condition is
not met, the optimization can cause unnecessary overhead in another workload
compared to the ideal workload.

### Hardware and Operating System Effects

**Why can matrix calculation time hide allocation improvements?**

Since the allocator versions do not change the matrix arithmetic, we look at
Amdahl's law [2]. It states that an improvement to allocation is capped by
allocation's share of total runtime. Matrix multiplication has O(n^3)
arithmetic over O(n^2) memory. This means that as the matrix grows, the
allocation share shrinks toward zero.

**Several threads update adjacent objects. How could padding each object to a
cache-line boundary waste space yet improve performance by reducing false
sharing and cache coherence traffic?**

Cache coherence works on whole cache lines [3]. So, when two threads write to
objects that share a line, each write invalidates the other thread's copy and
the line bounces between them. Padding each object to a cache-line boundary
wastes space, but it eliminates that false sharing by trading cheap memory for
expensive coherence traffic that gets worse as thread count rises.

### Software Engineering Practice

**How could namespaces support multiple allocators based on scope and
purpose?**

Namespaces let each subsystem use an allocator suited to its purpose. Scoping
allocators this way also isolates each subsystem's statistics and failures,
and a single namespace can swap a module's allocator without changing its
code.

**What tradeoffs come with creating and maintaining a custom allocator?**

A custom allocator can help maximize the efficiency of the program by reducing
the number of system calls and potentially memory fragmentation. However, if
the task is trivial, then the overhead from creating and maintaining the
custom allocator could slow down the entire process. Overhead includes both
runtime overhead and the overhead of writing, testing, and maintaining the
custom allocator. The additional code can be complex and hard to read, which
makes maintenance harder than using system calls.

**Why do good design, separation of concerns, portability, and reusability
matter when code is shared across projects?**

Shared code must be readable and maintainable by people who did not write it.
This allows anyone to understand what a change will affect. Portability was a
constraint in this project because the various environments handled the source
code differently.

**Explain the importance of single source of truth in source code
management.**

A single source of truth means each piece of information is defined in exactly
one authoritative place. This removes any ambiguity about which version is
current when several people edit the same file.

### Sources

1. P. R. Wilson, M. S. Johnstone, M. Neely, and D. Boles, "Dynamic Storage
   Allocation: A Survey and Critical Review," in *Proc. Int. Workshop on
   Memory Management (IWMM)*, LNCS vol. 986, Springer, 1995, pp. 1-116.
2. G. M. Amdahl, "Validity of the Single Processor Approach to Achieving Large
   Scale Computing Capabilities," in *Proc. AFIPS Spring Joint Computer
   Conf.*, 1967, pp. 483-485.
3. J. L. Hennessy and D. A. Patterson, *Computer Architecture: A Quantitative
   Approach*, 6th ed. Morgan Kaufmann, 2019.
