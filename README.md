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
| v8.0.0\|Matrix Array\|1 | Machine ID: mohamed-m3max-v8-full \| Averages | arg1=360 |
| v7.0.0\|Matrix Array\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on AMD Ryzen 9 7900X 12-Core Processor \| 32GB \| WSL Ubuntu 24.04 LTS \| Averages | — |
| v7.0.0\|Uniform Nodes\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on AMD Ryzen 9 7900X 12-Core Processor \| 32GB \| WSL Ubuntu 24.04 LTS \| Averages | — |
| v7.0.0\|Memory Stress\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on AMD Ryzen 9 7900X 12-Core Processor \| 32GB \| WSL Ubuntu 24.04 LTS \| Averages | — |
| v7.0.0\|Linked List\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on AMD Ryzen 9 7900X 12-Core Processor \| 32GB \| WSL Ubuntu 24.04 LTS \| Averages | — |
| v7.0.0\|Matrix Array\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v6.0.0\|Matrix Array\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on 12 core Apple M3 Max \| Not Collected \| 48GB \| MacOS 26.5.2, build 25F84 \| Averages | — |
| v6.0.0\|Uniform Nodes\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on 12 core Apple M3 Max \| Not Collected \| 48GB \| MacOS 26.5.2, build 25F84 \| Averages | — |
| v6.0.0\|Memory Stress\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on 12 core Apple M3 Max \| Not Collected \| 48GB \| MacOS 26.5.2, build 25F84 \| Averages | — |
| v6.0.0\|Linked List\|1 | Assignee: \| Mohamed Konsowa \| Group 2 \| Run on 12 core Apple M3 Max \| Not Collected \| 48GB \| MacOS 26.5.2, build 25F84 \| Averages | — |
| v6.0.0\|Matrix Array\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v5.0.0\|Matrix Array\|1 | Averages \| Using an Intel i7-11800H 8 core 16 thread @ 2.3 GHz up to 4.6 GHz | — |
| v5.0.0\|Uniform Nodes\|1 | AMD Ryzen 7 7800X3D (Zen 4) \| Ubuntu 26.04 (WSL2), glibc, g++ 15.2.0 | Short (size 100, 35,000 passes); Medium (size 100, 1,335,000 passes); Long (size 100, 4,100,000 passes) |
| v5.0.0\|Uniform Nodes\|2 | MacBook Pro Apple M5 Pro (arm64) \| macOS 26.6.2, Apple Clang, 24 GB | Short (size 100, 35,000 passes); Medium (size 100, 1,335,000 passes); Long (size 100, 4,100,000 passes) |
| v5.0.0\|Memory Stress\|1 | Not specified | — |
| v5.0.0\|Linked List\|1 | Not specified | — |
| v5.0.0\|Matrix Array\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v5.0.0\|Uniform Nodes\|3 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v4.0.0\|Matrix Array\|1 | Not specified | — |
| v4.0.0\|Uniform Nodes\|1 | Assignee \| Jose Fuentes - Group 1 \| Ubuntu 26.04 (WSL2), glibc, g++ 15.2.0 \| AMD Ryzen 7 7800X3D (Zen 4) \| Averages | Short  (size 100, 35,000 passes); Medium  (size 100, 1,335,000 passes); Long  (size 100, 4,100,000 passes) |
| v4.0.0\|Uniform Nodes\|2 | Assignee \| Jose Fuentes - Group 1 \| macOS 26.6.2, Apple Clang, 24 GB \| MacBook Pro M5 Pro (arm64) \| Averages (mean of 5 runs) | Short (size 100, 35,000 passes); Medium (size 100, 1,335,000 passes); Long (size 100, 4,100,000 passes) |
| v4.0.0\|Memory Stress\|1 | Not specified | — |
| v4.0.0\|Linked List\|1 | Not specified | — |
| v4.0.0\|Matrix Array\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v4.0.0\|Uniform Nodes\|3 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v3.0.0\|Matrix Array\|1 | Thinkpad X13 Yoga Gen 1 \| 16 GB of RAM \| Using WSL (Windows Subsystem for Linux) \| 4-core, 8-thread mobile processor with a base clock of 1.8 GHz \| Averages | — |
| v3.0.0\|Uniform Nodes\|1 | Not specified | Short (225 x 225), 600 passes; Medium (800 x 800), 600 passes |
| v3.0.0\|Memory Stress\|1 | Not specified | Short (200 rounds); Medium (1000 rounds; longer duration ones not needed due to obvious gap where regular is linear, but overloaded appears not to be) |
| v3.0.0\|Linked List\|1 | Not specified | — |
| v3.0.0\|Matrix Array\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v2.0.0\|Matrix Array\|1 | Assignee: \| Jacob Nance - Team 2 \| Run on 4 consecutive 11th Gen Intel® Core™ i7-1165G7  processors \| 16GB Memory \| Ubuntu 24.04.3 LTS  OS \| Averages | Short = 275 \| Med = 900 \| Long = 1225 |
| v2.0.0\|Uniform Nodes\|1 | Assignee: \| Jacob Nance - Team 2 \| Run on 4 consecutive 11th Gen Intel® Core™ i7-1165G7  processors \| 16GB Memory \| Ubuntu 24.04.3 LTS  OS \| Averages | Arg1 \| Short = 285 \| Med = 900 \| Large = 1200; All = 600 \| Averages |
| v2.0.0\|Memory Stress\|1 | Assignee: \| Jacob Nance - Team 2 \| Run on 4 consecutive 11th Gen Intel® Core™ i7-1165G7  processors \| 16GB Memory \| Ubuntu 24.04.3 LTS  OS \| Averages | Short = 100 \| Med = 440 \| Long = 900 |
| v2.0.0\|Linked List\|1 | Assignee: \| Jacob Nance - Team 2 \| Run on 4 consecutive 11th Gen Intel® Core™ i7-1165G7  processors \| 16GB Memory \| Ubuntu 24.04.3 LTS  OS \| Averages | Short = 125000 \| Med = 580000 \| Long = 875000 |
| v2.0.0\|Matrix Array\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |
| v1.0.0\|Matrix Array\|1 | Not specified | — |
| v1.0.0\|Uniform Nodes\|1 | Not specified | — |
| v1.0.0\|Memory Stress\|1 | Not specified | — |
| v1.0.0\|Linked List\|1 | Not specified | — |
| v1.0.0\|Matrix Array\|2 | Assignee: \| Liam Seymour, Group 1 \| Intel i5-6400, 4 logical cores \| 12 GB RAM \| Arch Linux (Kernel 7.2.4) \| Averages | — |

### Analysis Summary

| Table ID | Summary |
| --- | --- |
| v8.0.0\|Matrix Array\|1 | Matrix Array (environment 1): overloaded runtime changed -4.87%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.01301). |
| v7.0.0\|Matrix Array\|1 | Matrix Array (environment 1): overloaded runtime changed 9.73%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001226). |
| v7.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): overloaded runtime changed 4.48%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0007384). |
| v7.0.0\|Memory Stress\|1 | Memory Stress (environment 1): overloaded runtime changed 9.68%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0009381). |
| v7.0.0\|Linked List\|1 | Linked List (environment 1): overloaded runtime changed 12.08%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0007449). |
| v7.0.0\|Matrix Array\|2 | Matrix Array (environment 2): overloaded runtime changed 5.10%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001422). |
| v6.0.0\|Matrix Array\|1 | Matrix Array (environment 1): overloaded runtime changed -2.34%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0008068). |
| v6.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): overloaded runtime changed 6.40%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0007226). |
| v6.0.0\|Memory Stress\|1 | Memory Stress (environment 1): overloaded runtime changed -3.06%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0008024). |
| v6.0.0\|Linked List\|1 | Linked List (environment 1): overloaded runtime changed 0.24%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0004065). |
| v6.0.0\|Matrix Array\|2 | Matrix Array (environment 2): overloaded runtime changed 6.52%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001404). |
| v5.0.0\|Matrix Array\|1 | Matrix Array (environment 1): overloaded runtime changed 0.37%; did not improve. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.7255). |
| v5.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): insufficient paired runtime data. |
| v5.0.0\|Uniform Nodes\|2 | Uniform Nodes (environment 2): insufficient paired runtime data. |
| v5.0.0\|Memory Stress\|1 | Memory Stress (environment 1): insufficient paired runtime data. |
| v5.0.0\|Linked List\|1 | Linked List (environment 1): insufficient paired runtime data. |
| v5.0.0\|Matrix Array\|2 | Matrix Array (environment 2): overloaded runtime changed -6.44%; improved. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.4695). |
| v5.0.0\|Uniform Nodes\|3 | Uniform Nodes (environment 3): overloaded runtime changed 5.39%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001816). |
| v4.0.0\|Matrix Array\|1 | Matrix Array (environment 1): overloaded runtime changed -1.79%; improved. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.6398). |
| v4.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): insufficient paired runtime data. |
| v4.0.0\|Uniform Nodes\|2 | Uniform Nodes (environment 2): insufficient paired runtime data. |
| v4.0.0\|Memory Stress\|1 | Memory Stress (environment 1): insufficient paired runtime data. |
| v4.0.0\|Linked List\|1 | Linked List (environment 1): insufficient paired runtime data. |
| v4.0.0\|Matrix Array\|2 | Matrix Array (environment 2): overloaded runtime changed -0.80%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.02894). |
| v4.0.0\|Uniform Nodes\|3 | Uniform Nodes (environment 3): overloaded runtime changed 2.55%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.008073). |
| v3.0.0\|Matrix Array\|1 | Matrix Array (environment 1): insufficient paired runtime data. |
| v3.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): insufficient paired runtime data. |
| v3.0.0\|Memory Stress\|1 | Memory Stress (environment 1): insufficient paired runtime data. |
| v3.0.0\|Linked List\|1 | Linked List (environment 1): insufficient paired runtime data. |
| v3.0.0\|Matrix Array\|2 | Matrix Array (environment 2): overloaded runtime changed 0.66%; did not improve. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.2328). |
| v2.0.0\|Matrix Array\|1 | Matrix Array (environment 1): overloaded runtime changed -13.63%; improved. Regular vs overloaded repeated-measures ANOVA: not significant (p=0.073). |
| v2.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): overloaded runtime changed -7.02%; improved. Regular vs overloaded repeated-measures ANOVA: significant (p=0.04021). |
| v2.0.0\|Memory Stress\|1 | Memory Stress (environment 1): overloaded runtime changed 2333.61%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0007268). |
| v2.0.0\|Linked List\|1 | Linked List (environment 1): overloaded runtime changed 32457.14%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.0006808). |
| v2.0.0\|Matrix Array\|2 | Matrix Array (environment 2): overloaded runtime changed 3.81%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.001308). |
| v1.0.0\|Matrix Array\|1 | Matrix Array (environment 1): insufficient paired runtime data. |
| v1.0.0\|Uniform Nodes\|1 | Uniform Nodes (environment 1): insufficient paired runtime data. |
| v1.0.0\|Memory Stress\|1 | Memory Stress (environment 1): insufficient paired runtime data. |
| v1.0.0\|Linked List\|1 | Linked List (environment 1): insufficient paired runtime data. |
| v1.0.0\|Matrix Array\|2 | Matrix Array (environment 2): overloaded runtime changed 22.58%; did not improve. Regular vs overloaded repeated-measures ANOVA: significant (p=0.01417). |

