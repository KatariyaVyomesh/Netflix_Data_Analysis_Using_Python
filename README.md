
# 🎬 Netflix Content Analysis Dashboard

![Netflix Banner](https://img.icons8.com/color/452/netflix-desktop-app.png)

> **“Visualizing the global entertainment landscape—one title at a time.”**

A detailed exploratory data analysis (EDA) on Netflix's content library using **Python**, **pandas**, **matplotlib**, and **seaborn** to uncover key trends in movies and TV shows.

---

## 📚 Table of Contents

1. [📌 Project Overview](#-project-overview)  
2. [🛠️ Tech Stack](#️-tech-stack)  
3. [📈 Visual Insights](#-visual-insights)  
4. [📊 Python Code by Question](#-python-code-by-question)  
5. [🔍 Key Findings](#-key-findings)  
6. [📁 Dataset Info](#-dataset-info)  
7. [🚀 How to Run](#-how-to-run)  
8. [📸 Sample Visuals](#-sample-visuals)  
9. [🙌 Let's Connect](#-lets-connect)

---

## 📌 Project Overview

This project aims to perform an in-depth data analysis of Netflix's content catalog. It answers business and consumer-focused questions such as:

- What are the top genres on Netflix?
- When was the most content added?
- Who are the most featured actors?
- Which countries produce the most content?

---

## 🛠️ Tech Stack

| Tool            | Purpose                            |
|-----------------|------------------------------------|
| **Python**      | Programming language               |
| **pandas**      | Data manipulation & preprocessing  |
| **matplotlib**  | Data visualization (plots)         |
| **seaborn**     | Statistical visualizations         |
| **Jupyter/VS Code** | IDE for running scripts        |

---

## 📈 Visual Insights

The project includes 11 professional visualizations:

| # | Chart Title                            | Purpose                                        |
|---|----------------------------------------|------------------------------------------------|
| 1 | Top 5 Movie Genres                     | Popular movie content genres                   |
| 2 | Top 5 TV Show Genres                   | Popular TV show genres                         |
| 3 | Content Added by Year                  | Trends in Netflix’s content addition           |
| 4 | Top 10 Actors/Actresses                | Most frequently appearing cast members         |
| 5 | Total Movie Duration by Country        | Countries producing the longest movies         |
| 6 | Total TV Show Seasons by Country       | Countries with most TV seasons                 |
| 7 | Average Release Year by Type           | Evolution of content release years             |
| 8 | Content Rating Distribution (Pie)      | Certification breakdown                        |
| 9 | Content Added by Month (Line)          | Monthly release patterns                       |
|10 | Movie Duration Distribution (Histogram)| Insights into movie length                     |
|11 | TV Show Seasons Distribution           | Number of seasons per show                     |

---

## 📊 Python Code by Question

### ✅ Question 1: What are the top 5 genres for movies and TV shows?
```python
movie_genres = df[df['type']=='Movie']['genres'].str.split(',').explode().str.strip()
tvshow_genres = df[df['type']=='TV Show']['genres'].str.split(',').explode().str.strip()
movie_genre_counts = movie_genres.value_counts().head(5)
tvshow_genre_counts = tvshow_genres.value_counts().head(5)
```

### ✅ Question 2: How much content is added each year?
```python
yearly_content = df.groupby(['year_added', 'type']).size().unstack()
```

### ✅ Question 3: Who are the top 10 most featured actors or actresses?
```python
top_actors = df['cast'].str.split(', ').explode().value_counts().head(10)
```

### ✅ Question 4: Which countries have the longest movie durations?
```python
movie_duration = df[df['type']=='Movie'].groupby('country')['duration'].sum().sort_values(ascending=False).head(10)
```

//ignore      -      -----------------------------------------
### Content Strategy Analysis
![Content Timeline](images/netflix_images/content_added_by_year.png)  
*Fig 1. Content acquisition peaked in 2019 during the streaming wars*
```


### ✅ Question 5: Which countries have the most seasons of TV shows?
```python
tv_duration = df[df['type']=='TV Show'].groupby('country')['duration'].sum().sort_values(ascending=False).head(10)
```

### ✅ Question 6: What is the average release year of content by type?
```python
avg_release = df.groupby('type')['release_year'].mean()
```

### ✅ Question 7: What is the distribution of ratings?
```python
rating_counts = df['rating'].value_counts()
```

### ✅ Question 8: In which months does Netflix add the most content?
```python
df['month_added'] = pd.to_datetime(df['date_added'], errors='coerce').dt.month_name()
monthly_additions = df['month_added'].value_counts().reindex([
    'January', 'February', 'March', 'April', 'May', 'June', 
    'July', 'August', 'September', 'October', 'November', 'December'
])
```

### ✅ Question 9: What is the distribution of movie durations?
```python
movies = df[df['type'] == 'Movie']
sns.histplot(movies['duration'], bins=30, kde=True)
```

### ✅ Question 10: What is the distribution of TV Show seasons?
```python
tv_shows = df[df['type'] == 'TV Show']
sns.histplot(tv_shows['duration'], bins=15, kde=True)
```

### ✅ Question 11: What is the proportion of content type?
```python
type_counts = df['type'].value_counts()
```

---

## 🔍 Key Findings

📌 **Most Popular Genres**  
- Movies: *International Movies*  
- TV Shows: *International TV Shows*

📌 **Content Boom**  
- Peak year: **2019** with the highest content additions

📌 **Frequent Faces**  
- Most featured actor: **David Attenborough**

📌 **Country-Wise Content**  
- **USA** dominates in both total movie duration and TV show seasons

📌 **Content Type Proportion**  
- Majority content type: **Movies**

📌 **Ratings**  
- Most common rating: **TV-MA**

---

## 📁 Dataset Info

- **Source**: Netflix Titles Dataset  
- **Format**: CSV  
- **Columns**: Title, Cast, Director, Country, Date Added, Rating, Duration, Type, Genre, etc.  
- **Rows**: Thousands of entries from Netflix’s global library

---

## 🚀 How to Run

```bash
# Step 1: Clone the repository
git clone https://github.com/KatariyaVyomesh/Netflix_Data_Analysis_Using_Pandas/Netflix_Project

# Step 3: Install required packages
pip install pandas matplotlib seaborn

# Step 4: Run the script
python Netflix_Project.ipynb
```

---


## 🙌 Let's Connect

If you like this project, feel free to ⭐ it and connect with me:

📧 Email: mr.vyomesh.katariya@gmail.com  
🌐 GitHub: [KatariyaVyomesh](https://github.com/KatariyaVyomesh)  
💼 LinkedIn: [Vyomesh Katariya](https://www.linkedin.com/in/vyomesh-katariya)  
