# site-generator-speed-01-run-20261122

[![make.fun](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/davlermid/site-generator-speed-01-run-20261122/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/davlermid/site-generator-speed-01-run-20261122/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)

A faster drop-in for makefun-site 1.0.0, entered in
[make.fun's site-generator-speed-01-run-20261122](https://make.fun/bounty/site-generator-speed-01-run-20261122):
`solve.js` is a dependency-free ES module whose `run(input)` returns exactly the output
tree makefun-site 1.0.0's build returns for every case's site — each page's index.html,
the index and tag pages, build-report.txt and each static file, byte for byte.

The speed comes from bulk text handling: plain runs are HTML-escaped in one pass instead
of char by char, Markdown lines are classified by direct character scans instead of a
regex battery, word counts are tallied without materialising the words, slugs take an
ASCII fast path that skips Unicode normalisation, and repeated lookups (tag slugs, link
paths) are memoised inside each call. Nothing is kept between calls: each case is
answered alone.

Run with Node 22:

    MAKEFUN_INPUT_DIR=<kit>/practice/input MAKEFUN_OUTPUT_DIR=out node main.ts

`main.ts` reads every case from `cases.json`, answers each with `run`, and writes
`answers.json`.
