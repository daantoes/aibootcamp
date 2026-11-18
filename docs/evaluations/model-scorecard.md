# Model scorecard — rule R1 (pensionableSalary)

> One run is a sample, not a benchmark. Synthetic data only — never paste secrets or real member data.

| | Model A | Model B |
|---|---|---|
| Model (name as shown in the picker) | GPT-6.1 Sol (user-reported) | Haiku 4.5 (user-reported) |
| Harness · Mode · Permissions | Copilot · Interactive · Manual | Copilot · Interactive · Manual |
| Reasoning effort | Not recorded | Not recorded |
| Date | 2026-11-18 | 2026-11-18 |

Harness, mode, and permissions above are retained from the workshop template; actual run settings were not independently confirmed.

## Scores

| Criterion | How to score | Model A | Model B |
|---|---|---|---|
| Correctness verified | Expected values that match the `node -e` output (x / 5) | 5/5 | 3/5 |
| Edge cases found | Which did it cover? franchise boundary · salary cap · part-time · below franchise → 0 · invalid factor (0 or > 1) · negative salary | Zero salary / below franchise; above salary cap with part-time factor; NaN salary; invalid factors 0 and 1.01. Missed exact franchise boundary and negative salary. | Zero salary / below franchise; exact franchise and one euro above; exact cap with part-time factor; above cap. Missed invalid factors and negative salary. |
| Hallucinations | Invented functions, parameters, files or rules? List them (none = 👍) | None identified in the supplied answer. | No invented functions, parameters, or files identified. Incorrect numerical expectations: 17546 at factor 1 was given as 1.01 instead of 1; 137800 at factor 0.5 was given as 60127.75 instead of 60127.5. Rounding does not add a cent. |
| Latency feel | fast / ok / slow | Not recorded | Not recorded |
| Cost / credits | Relative cost of the model (supported-models doc) — heavier model = more AI credits | Not recorded; relative cost not verified | Not recorded; relative cost not verified |

Cost reference: [Supported AI models in GitHub Copilot](https://docs.github.com/en/copilot/reference/ai-models/supported-models). No cost ranking is inferred from this run.

## Verification output

Model A — GPT-6.1 Sol:

```text
0 1 0
137801 0.6 72153
NaN 1 RangeError: fullTimeSalary must be a non-negative number
46000 0 RangeError: partTimeFactor must be greater than 0 and at most 1
46000 1.01 RangeError: partTimeFactor must be greater than 0 and at most 1
```

Model B — Haiku 4.5:

```text
0 1 0
17545 1 0
17546 1 1
137800 0.5 60127.5
200000 1 120255
```

These are the actual outputs from the two `node -e` checks in this session. Model B's supplied expectations disagreed with its output on rows 3 and 4.

## Verdict

- For **this kind of task** I would use: **Model A (GPT-6.1 Sol)**, provisionally, based on this sample.
- Because: all five expectations matched execution, including invalid-input errors; Model B matched three of five. The models proposed different inputs, so these scores are not a controlled comparison.
- Would I trust it **without** the `node -e` check? **No** — plausible-looking arithmetic was wrong in two Model B cases, and neither set covered negative salary.
- To make this a real benchmark I would need: identical prompts and a shared test set covering all boundaries and validation branches, multiple tasks and repeated runs per model, confirmed run settings, and measured latency and credit usage.
