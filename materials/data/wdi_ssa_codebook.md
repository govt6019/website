# Codebook: `wdi_ssa.csv`

One row per country in the World Bank's Sub-Saharan Africa region (code SSF),
n = 48, year 2021. Built 2026-10-25 from the World Bank API by
`scripts/make_wdi_ssa.R`, for the Linear regression II deck. Rebuilds
Pepinsky's under-5 mortality example on current data. 2021 is the last year
with oil rents published.

| Variable | World Bank code | Meaning | Units |
|---|---|---|---|
| `iso3` | | ISO 3166 alpha-3 country code | |
| `country` | | Country name (World Bank spelling) | |
| `year` | | Data year | 2021 |
| `u5mort` | `SH.DYN.MORT` | Under-5 mortality rate | deaths before age 5 per 1,000 live births |
| `goveff` | `GOV_WGI_GE.EST` | Government Effectiveness, Worldwide Governance Indicators | index, about -2.5 to 2.5; mean 0, SD 1 across all countries in the world |
| `gdppc` | `NY.GDP.PCAP.KD` | GDP per capita | constant 2015 US$ |
| `oilrents` | `NY.GDP.PETR.RT.ZS` | Oil rents | % of GDP |
| `urban` | `SP.URB.TOTL.IN.ZS` | Urban population | % of total population |

Empty cells are missing in the source. Eritrea and South Sudan have no
`gdppc` or `oilrents`. The deck uses the 46 complete rows throughout, so the
short and long regressions share one sample.
