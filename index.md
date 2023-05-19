# league-of-legneds
This is a project for DSC 80 at UCSD
by Joanne Pon and Justin Huang

---

## Introduction:
Introduction and Question Identification:
Our project chooses the data of League of Legend Competitive Matches. This data contains information of players and teams from League of Legends competitive matches. The question that we are interested in is does the average game duration differ significantly between different competitive regions in tier-one professional leagues in 2022? The reader of the website should pay attention to this question because the game duration is important for implementing strategies. Understanding the difference lets people make a more effective decision toward the games. There are 149400 rows and 123 columns in this dataset, and columns that are relevant to our questions are ‘gameid’, ‘gamelength’, ‘league’. The gameid column represents the unique identifier to each game. The gamelength column represents how long the game takes. The league in which the game was played. 

---

## Cleaning and EDA
- Data Cleaning:
We clean the data by only taking a specific list of leagues, since our analysis only wants the  leagues that are in tier 1. By cleaning the data, we can focus on the data that we want. It help us to analyze the information faster. 
```py
print(tier_1[['gameid', 'gamelength', 'league']].head().to_markdown(index=False))
```

| gameid           |   gamelength | league   |
|:-----------------|-------------:|:---------|
| 8401-8401_game_1 |         1365 | LPL      |
| 8401-8401_game_2 |         1444 | LPL      |
| 8402-8402_game_1 |         1893 | LPL      |
| 8402-8402_game_2 |         2271 | LPL      |
| 8402-8402_game_3 |         1900 | LPL      |


- Univariate Analysis:
This plot shows how many games in each interval of gamelength. Most of the games have a gamelength between 1500-2500, but there are still games that have a gamelength that close to zero or over 3000.
<iframe src="assets/fig1.html" width=800 height=600 frameBorder=0></iframe>

- Bivariate Analysis:
This plot shows the relationship between different leagues and their gamelength. In this plot, we can see that LPL and LCK have a gamelength that are much more than the other leagues.
<iframe src="assets/fig1.html" width=800 height=600 frameBorder=0></iframe>

- Interesting Aggregates:
This pivot table contains the information of the mean, count maximum, minimum, median, standard deviation, and variance of the gamelength for each league.
```py
print(tier_pivot[['mean', 'count', 'max', 'min', 'median', 'var', 'std']].to_markdown(index=False))
```
|    mean |   count |   max |   min |   median |      var |    std |
|--------:|--------:|------:|------:|---------:|---------:|-------:|
| 1974.09 |     243 |  2861 |  1275 |     1928 | 103768   | 322.13 |
| 2020.06 |     467 |  3326 |  1145 |     1957 | 129359   | 359.66 |
| 1981.59 |     306 |  3097 |  1308 |     1923 | 105827   | 325.31 |
| 1993.26 |     243 |  3293 |  1176 |     1952 | 130677   | 361.49 |
| 1921.77 |     214 |  3006 |  1137 |     1870 | 129998   | 360.55 |
| 1989.54 |     187 |  3351 |  1352 |     1930 | 109292   | 330.59 |
| 1893.44 |     786 |  3363 |  1150 |     1856 |  98536.1 | 313.9  |
| 1858.03 |     271 |  3047 |  1115 |     1809 | 116989   | 342.04 |
| 1800.96 |     323 |  2910 |  1071 |     1769 |  83092.6 | 288.26 |

---

## Assessment of Missingness:

---

## Hypothesis Testing:
- Null Hypothesis: There is no significant difference in the average game length between tier 1 leagues in League of Legends.
- Alternative hypothesis: There is a significant difference in the average game lengths between tier 1 leagues in League of Legends.
- Test statistic: T-test
- Significance level: 0.05
- P-value: 3.1489400690188618e-24
- The T test is a good choice for this question because we are comparing the means of groups. We choose 0.05 as our significant level is because we don’t have that much evidence to reject this null hypothesis. 
- We see that there is a significant difference in average game duration between different regions.

---
