# CORE IQ — Optimized Battery Export

Source: https://cognitivemetrics.com/test/CORE (Optimized battery)
Exported: 2026-09-22

## Contents

| # | Subtest | Code | Domain | Items | Time/question | Answers |
|---|---------|------|--------|-------|---------------|---------|
| 1 | Analogies | AG | Verbal Comprehension | 34 | 45s | official (correct_key embedded in page) |
| 2 | Matrix Reasoning | MR | Fluid Reasoning | 29 | 120s | official (correct_key embedded in page) |
| 3 | Graph Mapping | GM | Fluid Reasoning | 26 | 50s | server-side only — not exposed; answers pending |
| 4 | Figure Weights | FW | Fluid Reasoning | 30 | 45s | server-side only — not exposed; answers pending |
| 5 | Visual Puzzles | VP | Visual Spatial | 26 | 45s | server-side only — not exposed; answers pending |
| 6 | Spatial Awareness | SA | Visual Spatial | 21 | 45s | 11/21 official (input-mode answers leaked via answer1/answer2 fields); 9 choice items server-side |
| 7 | Quantitative Knowledge | QK | Quantitative Reasoning | 27 | 60s | official (correct_key embedded in page) |
| 8 | Digit Span | DS | Working Memory | — | —s | n/a — test is spoken aloud; skipped per requirements |

## Files

- `core_questions.json` — full structured data (questions, choices, images, official answer keys, per-item time limits)
- `markdown/` — human-readable per-subtest export with relative image links
- `images/<CODE>/` — all puzzle images (`question_*` = stem, `choice_*` = options, `example_*` = training items)

## Notes

- **Digit Span was skipped**: its instructions state "This test is spoken aloud" — audio-administered with runtime-randomized digit sequences (3 subtests × 8 items × 2 trials, 2–9 digits, 60s response window). There is no fixed question bank to download.
- **Answer keys**: Analogies, Matrix Reasoning and Quantitative Knowledge embed `correct_key` in the client page (captured verbatim). Graph Mapping, Figure Weights, Visual Puzzles and Spatial Awareness are scored server-side; their answer keys are never sent to the browser, so those items are exported with answers pending.
- **Per-question time limits**: AG 45s, MR 120s, GM 50s, FW 45s, VP 45s, SA 45s; QK varies per item (`seconds` field, default 60s).
- **VP (Visual Puzzles)** uses checkboxes — exactly 3 options per item. **MR** choice numbering 1–5. **QK** `answer10` field holds the question figure when present.
- Training examples (with official answers) are included for MR, FW, VP, GM.
- Question sets are stable across page loads (verified 3 loads each); only presentation order varies.