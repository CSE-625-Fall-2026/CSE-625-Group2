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
