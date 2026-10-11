# Synthetic Gen Z Banking-Experience Dataset

**Companion data repository** for the MSc dissertation:

> **Investigating AI Chatbots and Robo-Advisors in the Financial Relationship of Gen Z Customers in Kazakhstan & Central Asia: A Mixed Human-Synthetic Participant Study**
> Lev Kashkin (DMY25044) — MSc in Business Administration (BAED PG)
> CITY College, University of York Europe Campus
> Supervisor: Dr. Athanasios Kapoulas · November 2026

This repository contains the **complete synthetic-participant corpus** used in the
mixed human–synthetic design: verbatim prompts, generated responses, and the
reproducibility manifest. It is published so that any reader of the dissertation
can audit, re-run, or extend the experiment.

---

## Contents

| File | Rows | Format | Description |
|---|---:|---|---|
| `synthetic-responses-M2.csv` | 2 700 | long CSV | **Main corpus.** 20 personas × 3 models × 3 repetitions × 15 questions |
| `synthetic-responses-M2.json` | 180 | nested JSON | Same data as M2, keyed `persona\|model\|rep` → `{question: answer}` |
| `synthetic-responses-M1-pilot.csv` | 75 | long CSV | **Pilot** — 5 personas, single model, question-set validation |
| `synthetic-responses-M1-pilot.json` | 5 | nested JSON | Pilot raw output |
| `SHA256SUMS.txt` | — | text | Integrity checksums for every file above |
| `DATASET.md` | — | markdown | Full data dictionary and variables |
| `METADATA.md` | — | markdown | Provenance, models, cost, run log |
| `README.md` | — | markdown | This file |

---

## Design in one line

Twenty evidence-based Gen Z personas (Kazakhstan + Uzbekistan) were interviewed
by three large language models via a fixed 15-question protocol, each answer
repeated three times, to test whether synthetic respondents can **reproduce the
positions and arguments** of real Gen Z banking customers — and to document where
they **fail to reproduce the distribution**.

**Headline result:** synthetic respondents reproduce *thematic content* (what people
think) but **not the response distribution** (how many think it). Synthetic data is
therefore an *exploratory, hypothesis-generating* instrument — **not** a substitute
for real survey responses. See Chapters 4–5 of the dissertation.

---

## Reproduce

```bash
python -c "
import json
d = json.load(open('synthetic-responses-M2.json'))
k = 'P01|deepseek/deepseek-chat|r1'
print(d[k])          # 15 answers for persona P01, first repetition
"
```

The exact system prompt, user template, and generation parameters are reproduced
verbatim in **Appendix A** of the dissertation and summarised in `METADATA.md`.

## Licence & citation

- Data released under **CC BY 4.0** — see `LICENSE`.
- Please cite via `CITATION.cff`.

## Ethics

- No human participants' personal data is contained here. Human responses were
  collected under a separate ethics approval and are **not** redistributed in this
  repository (they are available in summary form only, in the dissertation).
- The synthetic corpus is clearly labelled as machine-generated throughout.
