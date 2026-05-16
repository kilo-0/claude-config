---
name: project_assessment011
description: Status of ARU Python assessment Element 011 — detailed per-question status, bugs, and missing items (updated 2026-03-29)
type: project
---

Assessment Element 011 — World Happiness Report EDA (12 questions, Jupyter notebook)
File: C:\Users\kilo_\OneDrive\Desktop\ARU\2- Programming with Python (2025 MOD009735 TRI2 D01NON)\anaconda\python\Asessment 011.ipynb
Total cells: 171

**Status as of 2026-03-29 (full notebook read):**

- Q1 (happiest/unhappiest): MOSTLY COMPLETE. Bar chart produced, findings text written (~85 words, good). Bug: cell 23 uses `.iloc[[0,-1]]` on sorted subset — this picks the first row of Denmark data (2005) and last row of South Sudan data (2017), not the country averages. The chart shows single data points rather than the computed averages from `avg`. Should use the `avg` DataFrame directly for the bar chart.

- Q2 (top/bottom 10 trends over time): PARTIAL. Line chart of all 20 countries over time (cell 42) is good. Grouped bar chart comparing historical avg vs 2021 score (cell 49) is good. Missing: NO findings/discussion text written at all. Brief says "2024 score" but only 2021 data used (acceptable given datasets provided). The `historical` variable used in the line chart is df1-only (excludes 2021), which is appropriate.

- Q3 (life expectancy + GDP vs happiness): MOSTLY COMPLETE. Two scatter plots produced (cells 54-55). Missing: NO findings/discussion text. The question also mentions a "correlation matrix" as an option — not used but scatter plots satisfy the brief. Column name used is 'Healthy life expectancy' (df2) — correct.

- Q4 (regional happiness): MOSTLY COMPLETE. Bar chart of regional averages produced. Missing: NO findings/discussion text. Minor: used a for loop + dict to compute region means (cells 63-64) when `df2.groupby('Regional indicator')['Ladder score'].mean()` would be cleaner, but result is correct.

- Q5 (corruption + freedom): INCOMPLETE. Only corruption scatter plot produced (cell 70) — has country labels. Freedom variable ('Freedom to make life choices') NOT plotted at all, despite being available in both df1 and df2. Missing: NO findings/discussion text.

- Q6 (population/density vs happiness): COMPLETE. Sourced external dataset ('countries of the world.csv'), handled whitespace issue in country names (cell 82), fixed comma-as-decimal separator (cell 85), produced two labelled scatter plots with log scale (cells 91-92). Has findings text (cell 74). Good problem-solving. Minor: used `how='outer'` in merge (cell 83) then dropped NaN — `how='inner'` would be cleaner.

- Q7 (urban density): PARTIAL. Acknowledged data gap (cell 96). Sourced urban population % dataset, merged with df1, produced scatter plot (cell 108). Has explanatory markdown. Cell 108 has a "to do" comment about country labels — labels not added. No findings/discussion written.

- Q8 (birth rate vs happiness): NOT DONE. Only a one-line findings note "no data available." No external dataset sourced, no plot. Should source birth rate data externally (e.g., World Bank) as done for Q6/Q7.

- Q9 (formerly happy / improved): COMPLETE and STRONGEST ANSWER. Horizontal bar charts for top 10 declined and top 10 improved (cells 124-125). Good methodology. Full findings text written (cell 126). Well structured.

- Q10 (COVID impact): PARTIALLY DONE BUT HAS A LOGIC BUG. Code exists (cells 128-147). Data setup correct: pre_covid (pre-2020 avg), covid (2020 scores), post_covid (2021 scores from df2). Bug: cells 136-137 apply `.abs()` to the SUBTRACTED column rather than to the RESULT of the subtraction — these intermediate columns are wrong (though cell 138's `overall_change` is computed correctly using `.abs()` on the difference). Final chart (cell 147) shows only 2 countries (most/least affected). Findings text written but says "-1.55" for Venezuela — the actual `overall_change` value computed is 1.23 (absolute), so the stated figure is inconsistent with the code. The interim columns `pre-during` and `during-post` are not used in the final answer, so the `.abs()` bug there does not affect the output — but it's conceptually wrong and would confuse a reader.

- Q11 (2008 financial crisis): DONE. Code exists (cells 151-161). Methodology: merged df1 with regional indicators from df2, grouped by region, compared pre/post 2008 averages. Bar chart produced (cell 160). One limitation: `pre_crisis` is `year < 2008` but df1 starts from 2005, so only 3 years of pre-crisis data. `crisis` variable (year==2008 data) is created but never used in the chart — only pre vs post averages compared. Has findings text (cell 162).

- Q12 (air quality/pollution): NOT DONE. 5 empty code cells. Only a comment with a World Bank data URL. No data loaded, no plot, no findings.

**Missing across the board:**
- Q2, Q3, Q4, Q5, Q7 all lack the required findings/discussion text (<100 words each)
- Q5 missing the freedom plot
- Q8 and Q12 completely empty (no external data sourced, no plots)

**Priority order for completion:** Q12 > Q8 > Q5 (add freedom plot + findings) > Q2/Q3/Q4/Q7 (add findings text) > fix Q1 chart bug

**Why:** Graded individual assignment. Submission via Canvas.
**How to apply:** When helping with this notebook, use the per-question status above to prioritise what to work on. Avoid rewriting working code unless asked.
