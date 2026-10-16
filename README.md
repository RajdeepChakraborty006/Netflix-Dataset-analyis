# Netflix-Dataset-analyis
This Netflix dataset has information about the TV shows and Movies available on Netflix till 2021. The dataset is collected from Flixable which is a third-party Netflix Search Engine &amp; available on Kaggle website for free.


# Netflix Content Analysis

Exploratory data analysis of Netflix's catalogue (7,789 titles) using Python. The project covers data cleaning, feature engineering, multi-value column handling, statistical analysis and visualisation to uncover trends in what Netflix adds, where it comes from, and how it is rated.

## Dataset

- **File:** `8__Netflix_Dataset.csv` (source: add the link here, e.g. Kaggle)
- **Size:** 7,789 rows × 11 columns
- **Columns:** `Show_Id`, `Category` (Movie / TV Show), `Title`, `Director`, `Cast`, `Country`, `Release_Date` (date added to Netflix), `Rating`, `Duration`, `Type` (genres), `Description`

## Tools and Libraries

Python · Pandas · NumPy · Matplotlib · Seaborn · WordCloud · Jupyter Notebook

## Project Workflow

1. **Data preparation:**
   - Handled nulls on a copy of the data (`Unknown` fill for Director, Cast and Country; dropped rows with missing Rating or Release_Date)
   - Split `Duration` into `duration_min` (movies) and `duration_season` (TV shows)
   - Extracted Year, Month and Day of Week from `Release_Date`
   - Grouped 14 ratings into 4 audience groups (Kids, Teens, Adults, Unrated)
2. **Basic exploration:** 14 questions on the raw data (directors, countries, ratings, releases per year)
3. **Multi-value columns:** `str.split()` + `explode()` to count genres, actors and countries correctly, plus the most frequent actor pair using `itertools.combinations`
4. **Aggregation:** pivot tables, `groupby`, `crosstab`, rolling averages
5. **NumPy statistics:** mean, median, std, percentiles; outlier detection with the IQR method and manual z-scores
6. **Labelling:** movie length categories using both `np.where()` and `pd.cut()`, with a comparison of the two
7. **Visualisation:** line chart, heatmap, boxplot, stacked bar chart, 2×2 dashboard and word clouds
8. **Insight questions:** TV Show trend, kids' content by country, season count vs genre and rating

## Key Findings

- Movies peaked in **2019 (1,498 titles added)** and TV Shows in **2020 (697)**.
- TV Shows make up ~31% of the catalogue, with **no clear shift** toward them over time.
- Netflix is adding **longer movies**: the average rose from ~83 min (2015-16) to ~100-107 min (2018 onward).
- Indian movies are the **longest (~126 min)**; Canada has the highest share of kids' content (24%); France skews most toward adult ratings (58%).
- The **US** produces the most kids' content by volume (375 titles).
- About **67% of TV shows have only one season**; longer-running shows skew toward kids' content and comedies.
- 336 movies are IQR outliers (e.g. *Bandersnatch*, 312 min). They are genuine titles, so they were kept.

## How to Run

```bash
pip install pandas numpy matplotlib seaborn wordcloud jupyter
jupyter notebook Netflix_dataset.ipynb
```

Place `8__Netflix_Dataset.csv` in the same folder as the notebook.

## Repository Structure

```
├── Netflix_dataset.ipynb
├── 8__Netflix_Dataset.csv
└── README.md
```

## Possible Extensions

- Predict whether a title is a Movie or TV Show from its description (text classification)
- Build a simple recommender based on genre and description similarity
- Create an interactive dashboard with Plotly or Streamlit
