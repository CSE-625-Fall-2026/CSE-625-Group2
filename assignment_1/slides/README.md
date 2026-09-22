# Allocator profiling: Beamer presentation and poster

## Contents

- `main.tex`: completed source based on the supplied Madrid/whale, 16:9 Beamer template. Includes all 30 frames in one file: 27 presentation slides and three appendices.
- `poster.tex`: matching single-page A0 landscape Beamer poster (118.9 × 84.1 cm).
- `Allocator_Profiling_Slides.pdf` and `Allocator_Profiling_Poster.pdf`: compiled deliverables.
- `figures/*.tex`: editable PGFPlots charts. Data are embedded in each figure source.
- `figures/report_pthreads_scaling.pdf`: the original report Figure 5, cropped without changing its data. Its original image resolution is preserved; raw plotting observations were not supplied.
- `data/`: full-precision v8 statistical results and the counts underlying the aggregate charts.

## Compile

Extract the entire project. Run from this directory:

```sh
pdflatex -interaction=nonstopmode -halt-on-error main.tex
pdflatex -interaction=nonstopmode -halt-on-error main.tex
pdflatex -interaction=nonstopmode -halt-on-error poster.tex
pdflatex -interaction=nonstopmode -halt-on-error poster.tex
```

In Overleaf, upload the whole ZIP and select `main.tex` for the slideshow or `poster.tex` for the poster. Use pdfLaTeX. Dependencies are standard TeX Live packages: beamer, beamerposter, lmodern, amsmath, amssymb, graphicx, booktabs, array, listings, and pgfplots with groupplots.

The attached `main(1).tex` was the template. Its title, authors, course, date, aspect ratio, and Madrid/whale theme were retained. Content is now self-contained in `main.tex`; unavailable external `sections/` files are no longer required. Figure files in `figures/` are required. The supplied report PDF is unchanged.

## Evidence map

| Slides | Evidence |
|---|---|
| 2–5 | Report I, IV, VI, XIV: research questions, workload choices, protocol and limitations. The 960-run design-space count is illustrative, not completed measurement coverage. |
| 6 | Report V, Tables II–V, XXII–XXIII and XII; updated v8 environment inventory. |
| 7 | Report VII and XII; updated v8 statistical methods. |
| 8–10 | Report III, Table I, VI: allocator and workload code descriptions. No new repository audit was performed. |
| 11 | Report Table VI: M3 Max size-360 short campaign, three runs per allocator and six concurrent processes per batch. This is distinct from the shared-workbook campaign. |
| 12–16 | Report XII, Tables XII–XXI and original Figure 5. Summary means, standard deviations and inferential p-values are reported values, not recomputed from unavailable pthread raw data. |
| 17 | Report III-J/K and XVI: matrix-focused v8 policy, incomplete linked-list runs. |
| 18–23 | Updated v8 runtime, exact directional tests, Welch environment comparison and metric results. |
| 24–25 | Updated chart_counts.json. All testable rows form denominators; missing and not-testable rows are excluded. Each row has equal weight. |
| 26–27 | Report XIV and conclusions qualified by the new v8 environment. |
| 28 | Two-condition repeated-measures ANOVA sums of squares calculated from E2's five pairs per run length. |
| 29 | Report Tables XIII/XVII and XIV/XVIII. |
| 30 | Source mapping and unresolved source inconsistencies. |

## Statistical interpretation

The user’s questions are answered directly without repeating unsupported premises:

- ANOVA and chi-square are separate tests. Paired ANOVA uses the magnitude of differences; the directional test counts their signs.
- V8 expected sign counts are below five. Exact two-sided binomial sign tests determine significance for both v8 groups. Approximate chi-square p-values are shown for comparison only. Non-v8 legacy directional results were not revalidated.
- Within v8 E2, pairing is inferred from alternating Regular/Overloaded records in each CSV cycle. Independent pairs and approximately normal differences are assumptions. V8 p-values use the unadjusted 0.05 threshold and are exploratory.
- Runtime percentage change is the mean of paired percentage changes. Metric percentage change is the percentage difference of means. These need not be numerically identical.
- Between v8 groups, Welch ANOVA compares paired percentage changes by run length. E1 and E2 differ in workload parameters and repetition strategy. The tests cannot attribute the difference solely to architecture or OS.
- The report does not support a blanket claim that CMA made pthreads much worse. Under native Linux, CMA v7 reduces pthreads v4 mean runtime by 29.15% with Tukey p<0.0001. WSL pthreads v6 worsens by 2.78% with p=0.0135. The other two allocator contrasts are not significant.
- Non-significant Shapiro–Wilk/Levene results do not prove normality or equal variance. Total runtime and resource counters cannot establish how much time was spent waiting on allocator locks or missing in cache.
- The report’s older v8 tables and conclusion describe the first environment. These slides include the second group. The report's Table V lists v2 medium matrix size as 800, whereas its inventory lists 900. The new v8 CSV independently specifies 400; the conflicting v2 parameter is not used in a new calculation.

## Method references

- NIST Sign Test: https://www.itl.nist.gov/div898/software/dataplot/refman1/auxillar/signtest.htm
- SciPy paired test: https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.ttest_rel.html
- SciPy one-way/Welch ANOVA: https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.f_oneway.html

The source contains selected speaker notes with additional caveats. Beamer hides these by default. The complete previous IEEE table package remains a separate deliverable; the slides use selected tables sized for presentation.
