# 🍿 Netflix Content Strategy Analysis: EDA & Feature Engineering

## 📌 Project Overview
This project performs an in-depth Exploratory Data Analysis (EDA) on Netflix's catalog to uncover structural shifts in their business model, audience targeting, and content lifespans. By applying advanced data wrangling techniques and statistical visualizations, this analysis answers critical business questions: *Is Netflix pivoting away from movies? Are Hollywood runtimes shrinking? And which TV genres actually survive the "Netflix Cancellation Curse"?*

## 🛠️ Tech Stack & Libraries
* **Python** (Data manipulation and logic)
* **Pandas** (Data cleaning, aggregation, cross-tabulation)
* **Seaborn & Matplotlib** (Statistical data visualization)

## 🧮 Key Data Handling & Engineering Techniques
Real-world data is messy, especially unstructured text. This project implements several robust cleaning and engineering steps before any visualization occurs:
1. **List Explosion (`.explode()`):** Unpacking comma-separated strings in the `listed_in` (Genres) and `country` columns to prevent data fracturing and ensure accurate category counting for co-productions.
2. **Feature Engineering:** Extracted unstructured text metrics by engineering a `desc_word_count` feature from the show descriptions.
3. **Discrete vs. Continuous Handling:** Overcame visualization traps (like "barcode" scatter plots) by aggregating discrete integer data (TV show seasons) using group-by means to track time-series trends accurately.
4. **Frequency Matrices:** Utilized `pd.crosstab()` to wrangle heavily skewed categorical data into clean mathematical grids for heatmapping.

---

## 📊 Key Insights & Visualizations

### 1. The Executive Pivot (Movies vs. TV Shows)
A macro-level view of Netflix's production strategy. The data reveals a massive strategic pivot starting around 2015, where the gap between Movie and TV Show production closed drastically, indicating a shift toward a serial-production model.
![Netflix Pivot Trend](Netflix%20Images/Final_Verdict/The%20Netflix%20Pivot%20Movies%20vs%20TV%20Shows%20Over%20Time%20(2000-Present).png) 


### 2. Global Producers & Target Audiences
By analyzing the top production countries and maturity ratings, the data highlights severe regional divergence (e.g., India's massive output of Movies vs. near-zero TV Shows) and proves a heavy platform bias toward mature (TV-MA) audiences across both formats.
![Global Producers](Netflix%20Images/Final_Verdict/Global%20Dominance%20Top%205%20Content%20Producers.png)
![Movies vs TVshow by Rating](Netflix%20Images/Final_Verdict/Target%20Audience%20%20Movies%20vs%20TV%20Shows%20by%20Rating.png)

### 3. TV Show Lifespans & The "Cancellation Curse"
Because the vast majority of Netflix shows are cancelled after a single season, standard boxplots collapse visually. Using aggregated multi-trendlines, we tracked the survival rate (average season count) of the Top 4 genres over time, revealing a massive drop-off in show lifespans post-2015.
![TV Show Survival Rate](Netflix%20Images/Multivariate/Survival%20Rate%20Average%20TV%20Show%20Lifespan%20by%20Genre%20(2010-Present).png)

### 4. Bypassing Skewed Data with Heatmaps
To visualize the intersection of Genres and Ratings without visual clutter, the data was transformed into a frequency matrix. This heatmap clearly maps exactly where specific genres cluster on the maturity scale.
![Genre vs Rating Heatmap for TV shows](Netflix%20Images/Bivariate/Heatmap%20Top%20Genre%20vs%20Top%20Ratings%20tv.png)
![Genre vs Rating Heatmap for Movies](Netflix%20Images/Bivariate/Heatmap%20Top%20Genre%20vs%20Top%20Ratings.png)

### 5. Hollywood vs. Bollywood: Runtime Convergence
Using multivariate scatter plots with calculated regression lines (`sns.lmplot`), we tracked the `duration_minutes` of movies over time to see if traditional 2.5-hour Indian epics are shrinking to match the 90-minute US standard.
![Movie Runtimes Over Time](Netflix%20Images/Multivariate/Hollywood%20vs%20Bollywood%20Movie%20Runtimes%20Over%20Time%20(2000-Present).png)

### 6. The ML Feature X-Ray (Pairplot Matrices)
To prepare the dataset for potential Machine Learning applications, all continuous and discrete numerical features (`release_year`, `duration_minutes`/`season_count`, and the engineered `desc_word_count`) were plotted in a Seaborn Pairplot. This revealed strict internal company rules, such as the perfect bell curve peaking at exactly 25-word descriptions for both movies and TV shows.
![Movies Pairplot](Netflix%20Images/Multivariate/Pairplot%20Matrix%20Numerical%20Features%20in%20Netflix%20Movies.png)
![Tv show Pairplot](Netflix%20Images/Multivariate/Pairplot%20Matrix%20%20Numerical%20Features%20in%20TV%20Shows.png)

---

## 🚀 How to Run the Notebook
1. Clone the repository to your local machine.
2. Ensure you have the required libraries installed: `pip install pandas matplotlib seaborn`
3. Download the Netflix dataset (CSV) and place it in the project root directory.
4. Run the Jupyter Notebook sequentially to view the data transformation pipeline and visualization outputs.