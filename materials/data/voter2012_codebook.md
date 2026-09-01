# Codebook: `voter2012.csv`

Subset of the **2012 VOTER Study** — a nationally representative survey of
public opinion in the United States. n = 8,000. Inherited from the Fall 2025
course materials (there it was `prelim_data.csv`).

**Deliberate teaching hazards** (do not "fix" these in the file — cleaning them
is the point of the labs):

- The four issue-importance items use **5 = Don't know**, which must be recoded
  to missing before any averaging.
- Two issue items are **reverse-framed** ("... is *not* an important issue").
- `pol_interest` hides its nonresponse as **4 = Not sure**.
- Age is not in the data — derive it from `birthyr` (survey year 2012).
- All variables arrive as bare integers; labels live only in this codebook.

| Variable | Question / meaning | Values |
|---|---|---|
| `important_econ` | "The economy is an important issue" (agreement) | 1 Strongly agree · 2 Agree · 3 Disagree · 4 Strongly disagree · 5 Don't know |
| `important_gayr` | "Gay rights are an important issue" (agreement) | same scale |
| `unimportant_budget` | "The budget deficit **is not** an important issue" (agreement — reverse-framed) | same scale |
| `unimportant_abort` | "Abortion **is not** an important issue" (agreement — reverse-framed) | same scale |
| `educ` | Highest education completed | 1 No HS · 2 HS grad · 3 Some college · 4 2-year · 5 4-year · 6 Post-grad |
| `birthyr` | Year of birth | 1921–1994 |
| `pol_interest` | Interest in politics and current affairs | 1 Not much · 2 Somewhat · 3 Very much · 4 Not sure |
| `pid3` | Party identification | 1 Democrat · 2 Republican · 3 Other |
| `gender` | Gender | 1 Man · 2 Woman |

Empty cells in the CSV are genuine item nonresponse (read as `NA`), *in
addition to* the disguised nonresponse codes above.
