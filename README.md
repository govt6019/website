# GOVT 6019: Introduction to Probability and Applied Statistics

**Course website: <https://govt6019.github.io/website/>**

This is the first course in the quantitative methods sequence in the Cornell Department of Government, and it also serves students in the Brooks School. It takes you from the basics of data and measurement, through probability and statistical inference, to the linear regression model and its interpretation.

The course meets twice a week. Seminar is Friday; discussion section is the Wednesday after, and works through the previous seminar's material in R.

## Repository structure

Everything you need is in `materials/`. The rest builds the website.

```
materials/               everything for the course
  syllabus.pdf           the syllabus, start here
  lectures/              seminar slides, as PDF (slides_w01.pdf, ...)
  discussion_section/    Wednesday lab materials, Quarto source and HTML
  homework/              weekly problem sets, Quarto source and PDF
  data/                  relevant data for the class
  scripts/               gov6019_ggplot.R, the course figure theme, and other scripts

web/                     website source, not needed for the course
  _quarto.yml            project configuration and navbar
  index.qmd              website home page
  schedule.qmd           website schedule, linking every week's materials
  readings.qmd           texts and week-by-week reading assignments
  setup.qmd              install R and Positron before the first section
  theme/                 LaTeX/Quarto theme files the sources need to render
```

The site is built and published by `.github/workflows/publish.yml` on every
push to `main`, so the rendered HTML is not committed and the repository holds
one copy of each file rather than two.

To preview locally, run `quarto render` from inside `web/`. Output goes to
`docs/`, which is ignored by git. Links to course materials will not resolve in
a local preview until you also run `cp -r materials docs/materials`, which is
what the workflow does.

Homework is ungraded, but you are strongly encouraged to do it properly anyway: the two in-class exams are
built in exactly this style, so it is the best exam preparation available.

Materials go up as we reach them, so pull (or re-download) before each week
rather than once at the start.
