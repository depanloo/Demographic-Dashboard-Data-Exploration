# 🏙️ Population Dashboard: Bandar Lampung by Sub-district and Sex (2023)

![Dashboard preview](hasil.jpg)

**TL;DR:** An interactive Google Looker Studio dashboard showing the 2023 population of Bandar Lampung's **20 sub-districts (*kecamatan*)** by sex, built during my internship at BPS Kota Bandar Lampung. The city has about **1.10 million residents**. **Kemiling** is the largest sub-district (86,300; 7.8% of the city) and **Enggal** the smallest (25,752). The five largest sub-districts hold **33.6%** of the population. The sex ratio is balanced (**102 men per 100 women**) and Enggal is the only sub-district with more women than men.

| | |
|---|---|
| **Tools** | Google Looker Studio (dashboard), Google Colab + pandas (loading and inspecting the data) |
| **Data** | BPS Kota Bandar Lampung, population by sex and sub-district, 2023 |
| **Context** | Internship (*Kerja Praktik*), Data Science Program, Institut Teknologi Sumatera, at BPS Kota Bandar Lampung, Jun–Aug 2024. Individual project. |
| **Live dashboard** | *Add Looker Studio public link here* |
| **Full report** | [Laporan KP (PDF, Bahasa Indonesia)](Laporan%20KP_Deyvan%20Loxefal.pdf) |

---

## 1. Context
Bandar Lampung is the capital of Lampung Province and its economic, education and government center. Its population grew by 19.01% (164,660 residents) between 2011 and 2020, according to a 2023 study of settlement change in the city (Wulansari, *Geodika* 7(1)). Rapid growth makes it harder to plan public services across sub-districts, and raw demographic tables are difficult for decision-makers to scan quickly. This project turns the BPS sub-district table into a simple dashboard that answers three questions:

1. How is the population distributed across the 20 sub-districts?
2. Which sub-districts are the largest and smallest?
3. How balanced is the distribution between men and women?

## 2. Data & Process
* **Source:** secondary data from the BPS Kota Bandar Lampung website, 2023, one row per sub-district with male, female and total population (`data penduduk.xlsx`, 20 rows).
* **Data check (done in this README):**
  * The `Total` column sums to **1,100,109**.
  * For **Langkapura**, male + female = 43,642 but the published `Total` is 43,372 (a 270 difference). The data is kept as published. Sub-district rankings use `Total`; sex shares use male + female (556,781 and 543,598; 1,100,379 combined). The row should be checked against the BPS source table.
  * This 2023 table is a different series from the 2020 Population Census count (1,166,066), so the two should not be compared directly.
* **Dashboard (Looker Studio, single page):**
  * A sub-district selector (all 20 listed).
  * Two bar charts (male, female) showing the 10 largest sub-districts.
  * A bar chart comparing male and female population per sub-district.
  * A Google Maps bubble map where each bubble is a sub-district and the bubble color shows its **total population** (legend from 25,752 to 86,300).

## 3. Key Findings
**Population size**

| Sub-district | Population | Share of city | Male share |
| :--- | ---: | ---: | ---: |
| Kemiling | 86,300 | 7.84% | 50.46% |
| Panjang | 74,858 | 6.80% | 50.99% |
| Sukabumi | 73,178 | 6.65% | 50.81% |
| Way Halim | 68,468 | 6.22% | 50.22% |
| Sukarame | 67,138 | 6.10% | 50.53% |
| … | | | |
| Enggal (smallest) | 25,752 | 2.34% | 49.52% |

* The largest sub-district (Kemiling) has **3.4× the population** of the smallest (Enggal). The median sub-district has about 52,900 residents.
* The **top five sub-districts hold 33.6%** of the city's population.

**Sex distribution**
* City-wide: **50.6% male / 49.4% female** (556,781 / 543,598), a sex ratio of **102.4**.
* The male share stays between **49.5% and 51.5%** in every sub-district, so the distribution is balanced everywhere.
* **Enggal is the only sub-district with more women than men** (13,000 vs 12,752, sex ratio 98.1).
* The highest male shares are in **Teluk Betung Timur** (51.54%, sex ratio 106.3), **Teluk Betung Barat** (51.41%) and **Bumi Waras** (51.40%).

## 4. Implications
These points follow from population counts only; they are starting points for planning, not recommendations backed by service data.

1. **Service capacity planning should start with the most populous sub-districts** (Kemiling, Panjang, Sukabumi, Way Halim, Sukarame). Absolute population is only one input: it needs to be combined with land area, growth over time and the number of existing facilities.
2. **No sex-based gap needs correcting at the headcount level.** The population is balanced in every sub-district. Equity questions (health, education, employment) need sex-specific service data, which this dataset does not contain.
3. **Keep the dashboard updated each year** so changes in the distribution can be tracked.

## 5. Limitations
* **One year only (2023):** no trends or growth by sub-district, so "fast-growing" areas cannot be identified from this data.
* **Counts, not density:** the dataset has no land area, so the dashboard shows population size, not population density. BPS publishes density and sex ratio in related sub-district tables, which could be added.
* **No age structure, migration, income or facility data.**
* **Data inconsistency in Langkapura** (see Section 2) and a different series from the 2020 Census.
* The bar charts on the dashboard show only the 10 largest sub-districts; the complete list is in `data penduduk.xlsx`.
* Descriptive analysis only.

## 6. Possible Next Steps
* Add land area to compute population density and show it on a choropleth map.
* Add multi-year BPS data to show growth by sub-district.
* Add age groups (e.g., school-age and elderly population) and match them with the number of schools and health facilities per sub-district.

## 7. Repository Structure
```
├── README.md
├── hasil.jpg                          # Dashboard screenshot
├── data penduduk.xlsx                 # 2023 population by sex, 20 sub-districts (BPS)
└── Laporan KP_Deyvan Loxefal.pdf      # Internship report (Bahasa Indonesia)
```
