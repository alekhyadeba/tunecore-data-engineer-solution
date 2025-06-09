# TuneCore Data Engineer Take-Home

## Overview

This project shows how I ingested and modeled music streaming data using Python and pandas, following Kimball dimensional modeling principles. I worked with three CSVs and built a basic star schema that can support analytical queries.

---

## Dataset

- `artists.csv` – Artist info like name, country, join_date
- `releases.csv` – Contains releases linked to artists
- `streams.csv` – Streaming activity tied to releases

---

## My Approach

1. **Ingestion**: Used pandas to load and clean the CSVs. Normalized column names for consistency.
2. **Cleaning**: Removed duplicates and made sure data linked properly (e.g., streams to releases to artists).
3. **Modeling**:
   - Created two dimension tables: `dim_artists`, `dim_releases`
   - Created one fact table: `fact_streams` (with stream_date, stream_count, etc.)
   - Used surrogate keys for artist and release
4. **Data Checks**: Made sure surrogate keys were unique and there were no nulls in critical fields. Also checked FK mappings.

---

## Output Tables

| Table         | Type      | Description                        |
|---------------|-----------|------------------------------------|
| `dim_artists` | Dimension | Artist metadata with artist_sk     |
| `dim_releases`| Dimension | Release info + artist_id + release_sk |
| `fact_streams`| Fact      | Streaming data with metrics and FKs |

---

## Tools

- Python 3.8
- pandas
- Jupyter Notebook
- CSV files for input

---

## How to Run

1. Download/unzip the files
2. Open `code_solution.ipynb` in Jupyter
3. Run the cells from top to bottom

All the tables are created in memory using pandas, no database needed.
