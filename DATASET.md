# DATASET.md — Data dictionary

## `synthetic-responses-M2.csv` (main corpus, 2 700 rows)

Long-format table. One row = one model's answer to one question for one persona
in one repetition.

| Column | Type | Example | Meaning |
|---|---|---|---|
| `persona_id` | string | `P01` | Persona identifier, `P01`–`P20` (see persona table below) |
| `model` | string | `deepseek/deepseek-chat` | Generating model (OpenRouter slug) |
| `repetition` | integer | `1` | Repetition index, 1–3 (temperature sampling) |
| `question_no` | integer | `3` | Fixed question number, 1–15 |
| `question` | text | `Опишите недавний случай…` | Question text (verbatim, as asked) |
| `response` | text | `Недавно я писала в чат…` | Model answer, verbatim, unedited |

**Grid:** 20 personas × 3 models × 3 repetitions × 15 questions = **2 700 rows**.
No missing cells: every persona/model/repetition answered every question.

## `synthetic-responses-M2.json` (180 keys)

```json
{
  "P01|deepseek/deepseek-chat|r1": {
      "<question 1 text>": "<answer>",
      "<question 2 text>": "<answer>",
      "…": "…"
  }
}
```

Key = `persona_id | model | rN`. Value = object mapping all 15 question texts to
answers. Equivalent to the CSV, indexed for programmatic access.

## `synthetic-responses-M1-pilot.csv` (75 rows)

Pilot run used to validate the question set and prompt before the full run.
5 personas, single model, no repetitions.

| Column | Meaning |
|---|---|
| `persona_id` | `P01`,`P09`,`P11`,`P15`,`P20` |
| `model` | pilot model invocations |
| `variation` | prompt-variation label (pilot only) |
| `question_no`, `question`, `response` | as above |

## Persona roster (P01–P20)

All personas are **fictional composites**, each grounded in published Gen Z /
Central Asian consumer research. No real individual is represented.

| ID | Age | Location | Profile |
|---|---|---|---|
| P01 | 23 | Almaty (KZ) | Design student |
| P02 | 25 | Almaty (KZ) | IT professional |
| P03 | 21 | Astana (KZ) | University student |
| P04 | 24 | Shymkent (KZ) | Services sector |
| P05 | 22 | Almaty (KZ) | Financially literate |
| P06 | 26 | Astana (KZ) | Civil servant |
| P07 | 20 | Almaty (KZ) | Part-time student |
| P08 | 27 | Tashkent (UZ) | Urban professional |
| P09 | 23 | Almaty (KZ) | Religious (halal finance) |
| P10 | 28 | Taraz (KZ) | Religious (riba-averse) |
| P11 | 25 | East-Kazakhstan village | Rural |
| P12 | 22 | Kyzylorda aul | Rural |
| P13 | 29 | Oral/Uralsk (KZ) | Late Gen Z |
| P14 | 18 | Almaty (KZ) | Early Gen Z |
| P15 | 24 | Almaty (KZ) | Privacy sceptic |
| P16 | 26 | Astana (KZ) | AI-distrustful |
| P17 | 21 | Almaty (KZ) | AI enthusiast |
| P18 | 23 | Shymkent (KZ) | Low income |
| P19 | 27 | Tashkent (UZ) | Low income (UZ) |
| P20 | 29 | Remote region | Low connectivity |

Full persona prompts are reproduced in Appendix A of the dissertation.

## Variable notes

- **`model`** — three generation backends retained for the final corpus:
  `deepseek/deepseek-chat`, `google/gemini-2.5-flash`, `openai/gpt-4o-mini`.
- **`repetition`** — temperature 0.9; repetitions capture sampling variance.
- **Response language** — Russian, matching the real human instrument language.
- **No post-editing** — responses are machine output, kept verbatim so readers can
  judge fluency, hedging, and failure modes directly.
