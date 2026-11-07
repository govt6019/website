# Codebook: `atus2025.csv`

Extract of the **2025 American Time Use Survey** (ATUS, Bureau of Labor
Statistics), linked for some respondents to the **November 2024 Current
Population Survey Voting and Registration Supplement** (Census Bureau). One row
per respondent, n = 6,146. Built 2026-11-03 by `scripts/make_atus2025.R`, for
Homework 9. Source files are in `data/atus2025_raw/` and `data/cps2024nov_raw/`.

Each ATUS respondent is one person aged 15 or older. The interviewer walks the
respondent through one day, the **diary day**, from 4 a.m. to 4 a.m. the next
day. Each activity is then coded into the ATUS activity lexicon. The minute
variables below are totals for the diary day. They range from 0 to 1,440.

| Variable | ATUS / CPS source | Meaning | Values |
|---|---|---|---|
| `id` | `TUCASEID` | ATUS case ID | 14 digits; read as text |
| `day` | `TUDIARYDAY` | Day of the week of the diary day | 1 Sunday, 2 Monday, 3 Tuesday, 4 Wednesday, 5 Thursday, 6 Friday, 7 Saturday |
| `holiday` | `TRHOLIDAY` | Diary day was a holiday | 1 = yes, 0 = no |
| `age` | `TEAGE` | Age | 15–85; 80 means 80–84, 85 means 85 or older |
| `female` | `TESEX` | Sex | 1 = female, 0 = male |
| `college` | `PEEDUCA` | Bachelor's degree or higher | 1 = `PEEDUCA` 43–46, 0 otherwise |
| `employed` | `TELFS` | Employed in the reference week | 1 = employed (at work or absent), 0 = unemployed or not in the labor force |
| `children` | `TRCHILDNUM` | Number of household children under 18 | 0–8 |
| `citizen` | `PRCITSHP` | Citizenship status | 1–5 (below) |
| `veteran` | `PEAFEVER` | Ever served on active duty in the U.S. Armed Forces | 1 = yes, 0 = no |
| `union` | `PEERNLAB` | Member of a labor union or similar employee association | 1 = yes, 0 = no; wage and salary workers only |
| `region` | `GEREG` | Census region | 1 Northeast, 2 Midwest, 3 South, 4 West |
| `voted` | `PES1` (Nov 2024 CPS) | Voted in the election of November 5, 2024 | 1 = yes, 0 = no; linked respondents only (below) |
| `registered` | `PES1`, `PES2` (Nov 2024 CPS) | Registered to vote in that election | 1 = voted or said registered, 0 = said not registered; linked respondents only |
| `sleep` | `t010101` | Sleeping | minutes |
| `work` | `t0501xx` | Working at a paid job, main and other jobs | minutes |
| `tv` | `t120303` | Watching television and movies (not religious) | minutes |
| `reading` | `t120312` | Reading for personal interest | minutes |
| `social` | `t1201xx` | Socializing and communicating with others | minutes |
| `volunteer` | `t15xxxx` | Volunteer activities, all of major category 15 | minutes |
| `religious` | `t14xxxx` | Religious and spiritual activities, all of major category 14 | minutes |

`citizen`: 1 native, born in the United States; 2 native, born in Puerto Rico
or another U.S. outlying area; 3 native, born abroad of a U.S. citizen parent;
4 foreign born, U.S. citizen by naturalization; 5 foreign born, not a U.S.
citizen.

## The link to the November 2024 vote

Each ATUS respondent comes from a household that finished its eight months in
the CPS two to five months before the diary day. For 588 respondents, that
final CPS interview was in November 2024, the month of the CPS Voting and
Registration Supplement. The script links these 588 to the supplement on
household ID (`HRHHID`, `HRHHID2`) and line number (`PULINENO`). All 588 match.
Their CPS ages agree with the supplement in every case.

`voted` is filled in for **509** respondents: the linked citizens aged 18 or
older who answered yes or no. Turnout among them is 84%. `voted` is missing for
everyone else: the 5,558 respondents with a different final CPS month, and
the linked respondents who were under 18 or not citizens, or who said "don't
know", refused or did not answer the supplement. The Census Bureau's published
turnout tables count supplement nonrespondents as non-voters. This extract sets
them to missing.

Self-reported turnout in the CPS is higher than official turnout. Some
respondents who did not vote say they did. Other household members can also
answer the supplement for the respondent.

## Notes

- **No October 2025 diaries.** Because of the lapse in appropriations from
  October 1 to November 12, 2025, the ATUS collected no data in October 2025.
  The diary days run from January to December 2025, October excepted.
- **Weekend days are oversampled.** By design, about half of the diaries fall on
  a Saturday or Sunday: 1,631 Sundays and 1,433 Saturdays against about 600
  of each weekday.
- **Unweighted.** The ATUS final weight (`TUFINLWGT`) is not in the extract.
  Means from this file describe the respondents, not the U.S. population.
- **Not every activity is on every diary.** Most respondents report no
  reading, volunteering or religious activity on the diary day. The share of
  respondents with any minutes: sleep almost 100%, TV 78%, paid work 31%,
  socializing 30%, reading 20%, religious 12%, volunteering 6%.
- `veteran` and `union` come from the final CPS interview, two to five months
  before the diary day. `veteran` is missing for 85 respondents: 84 aged 15 to
  17 and one other. The CPS asks the union question only of employed wage and
  salary workers. `union` is filled in for 3,030 respondents. 192 of them were
  not employed by the diary day.
- Variable definitions: the 2025 ATUS Interview and ATUS-CPS data dictionaries
  and the 2025 activity lexicon (in `data/atus2025_raw/`), and the November 2024
  CPS technical documentation (`data/cps2024nov_raw/cpsnov24_techdoc.pdf`).
