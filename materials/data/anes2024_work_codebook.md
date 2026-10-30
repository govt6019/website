# Codebook: `anes2024_work.csv`

Extract of the **2024 ANES Time Series Study** (American National Election
Studies), pre-election wave: usual weekly hours of work and age. One row per
respondent, n = 5,521. Built 2026-10-23 from
`anes_timeseries_2024_csv_20260519.csv` by `scripts/make_anes2024_work.R`, for
Homework 8.

The hours question was asked of respondents who had worked at some point in
the past 12 months:

> During the past 12 months, in the weeks worked, how many hours did you
> usually work each week?

| Variable | ANES source | Meaning | Values |
|---|---|---|---|
| `id` | `V240001` | Respondent ID | 6-digit integer |
| `hours` | `V241481` | Hours usually worked per week, past 12 months | as reported |
| `age` | `V241458x` | Age on Election Day | 18–80; 80 means 80 or older |

Empty cells are nonresponse. For `hours`, these are respondents who were not
asked or who refused or did not know; for `age`, respondents who refused or
whose birth date is missing. The ANES codes for these (all negative) were set
to missing in the extract.

Valid counts: `hours` 3,505; `age` 5,242; both 3,374. The hours answers are
as reported: no value was capped, recoded or dropped. They match
`anes2024_hours.csv`. Responses are unweighted.
