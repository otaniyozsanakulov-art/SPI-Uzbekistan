# Uzbekistan SPI v4.0 — Reproducible Audit and Analysis

## About this project

This repository provides a reproducible audit and analytical framework for Uzbekistan’s results in the World Bank **Statistical Performance Indicators (SPI)**.

The project is designed to verify the main numerical results presented in the scientific-practical report, reproduce key SPI calculations, and document the underlying World Bank sources and methodology.

## Main data source

The analysis is based on the official **World Bank SPI v4.0** data.

- Data update: **November 2025**
- Official repository: `worldbank/SPI`
- Pinned commit:

`2dd02f746cb4e2159281adc74d6865f948e90ce1`

Main source files:

- `03_output_data/SPI_index.csv`
- `03_output_data/SPI_data.csv`

Using a pinned commit ensures that the calculations remain reproducible even if the World Bank updates the repository in the future.

## Key results for Uzbekistan

| Indicator | 2023 | 2024 | Change |
|---|---:|---:|---:|
| P1 — Data Use | 90.0 | 90.0 | 0.0 |
| P2 — Data Services | 76.6 | 79.1 | +2.5 |
| P3 — Data Products | 85.0 | 80.1 | -4.9 |
| P4 — Data Sources | 63.3 | 68.2 | +4.9 |
| P5 — Data Infrastructure | 95.0 | 90.0 | -5.0 |
| **Overall SPI** | **81.99** | **81.49** | **-0.50** |

The decline in the overall SPI score in 2024 is mainly associated with changes in the P3 and P5 pillars.

## What the notebook does

The Google Colab notebook automatically:

1. Downloads the official World Bank SPI v4.0 data from the pinned commit.
2. Extracts Uzbekistan’s 2023 and 2024 results.
3. Recalculates the P1–P5 pillar scores.
4. Recomputes the overall SPI score.
5. Reviews the SDG-level structure of P3.
6. Reviews the main P4 and P5 indicators.
7. Compares report values with official World Bank values.
8. Assigns `PASS`, `WARN`, or `FAIL` audit statuses.
9. Exports audit outputs in CSV, JSON, and HTML formats.

## Audit status interpretation

`PASS` means that the value reported in the study is consistent with the selected World Bank SPI source and the defined rounding rule.

`WARN` does not necessarily mean that a value is incorrect. It indicates that an additional primary source may be required to verify the interpretation or cause of a change, for example IMF, UN SDG, ILOSTAT, Open Data Watch, or national metadata.

`FAIL` indicates a numerical inconsistency that requires review.

## Rounding rule

For report-level presentation, decimal values are rounded using the `ROUND_HALF_UP` convention.

Example:

`88.15 → 88.2`

This avoids differences that may arise from Python’s default floating-point rounding behavior.

## Reproducibility

The notebook can be opened in Google Colab and all calculations can be reproduced by running:

`Runtime → Run all`

The project is intentionally linked to a fixed World Bank SPI version and commit so that the results can be independently reproduced.

## Repository structure

- `UZBEKISTAN_SPI_v4_0_COLAB_AUDIT_FINAL.ipynb` — main reproducible audit notebook
- audit outputs — generated automatically when the notebook is executed

## Methodological note

The SPI is structured hierarchically:

`Indicators → Dimensions → Pillars → Overall SPI`

The overall SPI score is calculated as the arithmetic mean of the five pillars, each with equal weight.

Some calculations, including P3 and P4, use specific aggregation rules defined in the World Bank SPI methodology.

## Disclaimer

This repository is **not an official World Bank product**.

The analysis, verification procedures, and conditional scenarios presented here were prepared independently using publicly available World Bank SPI data and methodology.

Future World Bank SPI releases may revise historical values. For this reason, the analysis is anchored to the **SPI v4.0 pinned commit** shown above.
