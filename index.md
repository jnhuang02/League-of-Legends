# league-of-legends
This is a project for DSC 80 at UCSD
by Joanne Pon and Justin Huang

---

## Introduction:
Introduction and Question Identification:
We choose the league of legends dataset for our project.

-The question that we are interested in is does the average game duration differ significantly between different competitive leagues in tier-one professional leagues in 2022? 

-This question is important because it illustrates how efficient and fast games in certain leagues are. In competition, this can help out with planning what the expected time of each match in a certain league is, or perhaps it may suggest that certain leagues perform better than others as they end their games earlier. 

-There are 149400 rows and 123 columns in this dataset, and columns that are relevant to our questions are ‘gameid’, ‘gamelength’, ‘league’. The gameid column represents the unique identifier to each game. The gamelength column represents how long the game takes. The league in which the game was played. 

---

## Cleaning and EDA
- Data Cleaning:
We clean the data by only taking a specific list of leagues, since our analysis only wants the leagues that are in tier 1, which is 'LCK', 'LPL', 'LEC', 'LCS', 'PCS', 'VCS', 'CBLOL', 'LJL', 'LLA'. 
            Since we are only looking at gamelengths and league so far, we are only going to keep those two columns. GameID is also important. We notice that the gamelength for every single player in the same game is the same, which makes it redundent and repetivtive to keep repeating the same time for every player
            in the game. Therefore it's useful to only keep one unique gameid at a time.
            

| gameid           |   gamelength | league   |
|:-----------------|-------------:|:---------|
| 8401-8401_game_1 |         1365 | LPL      |
| 8401-8401_game_2 |         1444 | LPL      |
| 8402-8402_game_1 |         1893 | LPL      |
| 8402-8402_game_2 |         2271 | LPL      |
| 8402-8402_game_3 |         1900 | LPL      |


- Univariate Analysis:
The distribution of the game duration for competitive league matches looks to be uniform as it seems to be in a bell shaped form.
<p><iframe src="plot1.html" width=800 height=600 frameBorder=0></iframe></p>

- Bivariate Analysis:
As seen here, the distribution of the gamelengths of the leagues do vary, which suggest that there could potentially be significant difference
        in the gamelengths that each league has.
<p><iframe src="plot2.html" width=800 height=600 frameBorder=0></iframe></p>

- Interesting Aggregates:
This outlines the stats of all the maximum, minimum, standard deviation, variance, etc, of the game durations of each tier 1 league. From there
        we can deduce which leagues stand out from the rest which can better help accept or reject the null hypothesis.
        
| league   |   count |   max |    mean |   median |   min |    std |    var |
|:---------|--------:|------:|--------:|---------:|------:|-------:|-------:|
| CBLOL    |     243 |  2861 | 1974.09 |     1928 |  1275 | 322.13 | 103768 |
| LCK      |     467 |  3326 | 2020.06 |     1957 |  1145 | 359.66 | 129359 |
| LCS      |     306 |  3097 | 1981.59 |     1923 |  1308 | 325.31 | 105827 |
| LEC      |     243 |  3293 | 1993.26 |     1952 |  1176 | 361.49 | 130677 |
| LJL      |     214 |  3006 | 1921.77 |     1870 |  1137 | 360.55 | 129998 |

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
