# Data access and schema

The data are not stored in this Git repository. Download the publication workbook from the [supplementary-material section of the published article](https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2026.1765142/full#supplementary-material) and save it as:

```text
data/Supplementary Data.xlsx
```

Expected sheets:

1. `Supplementary Data` - variable codebook.
2. `Exp1 Delay Discounting` - 8,940 rows from 596 participants.
3. `Exp2 Probability Discounting` - 8,880 rows from 592 participants.

Each study sheet contains participant ID, age, household-income category, education in years, gender, HADS anxiety/depression/distress, self-rated health, ethnicity, race, reward amount, the study-specific independent variable, and relative subjective value (RSV).

Study 1 records delays in months. Study 2 records probability as a percentage; the analysis converts probability to odds against before calculating empirical AuC. The workbook contains final analytic samples and therefore does not contain the original attention-check variables needed to reconstruct exclusions.

The `.gitignore` intentionally blocks all files in this directory except this README.
