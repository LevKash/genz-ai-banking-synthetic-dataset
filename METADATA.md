# METADATA.md — Provenance & reproducibility manifest

## Study

| Field | Value |
|---|---|
| Title | Investigating AI Chatbots and Robo-Advisors in the Financial Relationship of Gen Z Customers in Kazakhstan & Central Asia |
| Subtitle | A Mixed Human-Synthetic Participant Study |
| Author | Lev Kashkin (DMY25044) |
| Degree | MSc in Business Administration (BAED PG) |
| Institution | CITY College, University of York Europe Campus |
| Supervisor | Dr. Athanasios Kapoulas |
| Submitted | November 2026 |
| Ethics reference | #193/1 |

## Two runs

| | M1 — Pilot | M2 — Main corpus |
|---|---|---|
| Purpose | Validate question set & prompt | Full factorial generation |
| Personas | 5 (P01, P09, P11, P15, P20) | 20 (P01–P20) |
| Models | 1 | 3 |
| Repetitions | 1 | 3 |
| Questions | 15 | 15 |
| Planned cells | 75 | 2 700 |
| Produced cells | 75 | 2 700 |
| Failures | 0 | 0 (final retained corpus) |
| Date | 2026-10-11 | 2026-10-11 |

## Generation parameters (M2)

| Parameter | Value |
|---|---|
| Models retained | `deepseek/deepseek-chat`, `google/gemini-2.5-flash`, `openai/gpt-4o-mini` |
| Temperature | 0.9 |
| `max_tokens` | 200 |
| Retry policy | up to 3 attempts per cell on transient error |
| Access | OpenRouter + Google AI free tier |
| System prompt | `"Ты — {persona}, {FRAME}"` (verbatim in Appendix A) |
| User turn | one of the 15 fixed questions (verbatim, Russian) |
| Output language | Russian |
| Post-processing | none — answers kept verbatim |

## Cost

Total generation cost for the retained corpus ≈ **US $0.12** (M1 + M2 combined),
using free-tier and low-cost hosted models. No paid annotation or human coding was
purchased.

## Response length (M2 summary)

| Statistic | Synthetic (M2) | Real human (N=36) |
|---|---|---|
| Mean words | ≈ 390 | ≈ 62 |
| Median words | ≈ 395 | ≈ 27 |
| Share < 40 words | 0.7 % | ≈ 57 % |

The ≈ 6.3× length gap is a documented fidelity limitation discussed in Chapter 5:
synthetic respondents over-elaborate relative to real Gen Z customers.

## Integrity

Every file in this repository is checksummed in `SHA256SUMS.txt`. To verify:

```bash
shasum -a 256 -c SHA256SUMS.txt
```

## Files

```
synthetic-responses-M2.csv         2 700 rows — main long-format corpus
synthetic-responses-M2.json          180 keys — indexed raw output
synthetic-responses-M1-pilot.csv      75 rows — pilot long-format
synthetic-responses-M1-pilot.json      5 keys — pilot raw output
SHA256SUMS.txt                            checksums
DATASET.md                                data dictionary
METADATA.md                               this file — provenance
CITATION.cff                              citation metadata
LICENSE                                   CC BY 4.0
README.md                                 overview
```

## Licence

Data: **CC BY 4.0** (see `LICENSE`). Code snippets in this repo: MIT.
