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
<p><iframe src="plot5.html" width=800 height=600 frameBorder=0></iframe></p>

- Bivariate Analysis:
As seen here, the distribution of the gamelengths of the leagues do vary, which suggest that there could potentially mean there are significant differences
        in the gamelengths that each league has.
<p><iframe src="plot2.html" width=800 height=600 frameBorder=0></iframe></p>

- Interesting Aggregates:
This outlines the stats of all the maximum, minimum, standard deviation, variance, etc, of the game durations of each tier 1 league. From there
        we can deduce which leagues stand out from the rest which can better help accept or reject the null hypothesis by looking at their stats.
        
| league   |   count |   max |    mean |   median |   min |    std |      var |
|:---------|--------:|------:|--------:|---------:|------:|-------:|---------:|
| CBLOL    |     243 |  2861 | 1974.09 |     1928 |  1275 | 322.13 | 103768   |
| LCK      |     467 |  3326 | 2020.06 |     1957 |  1145 | 359.66 | 129359   |
| LCS      |     306 |  3097 | 1981.59 |     1923 |  1308 | 325.31 | 105827   |
| LEC      |     243 |  3293 | 1993.26 |     1952 |  1176 | 361.49 | 130677   |
| LJL      |     214 |  3006 | 1921.77 |     1870 |  1137 | 360.55 | 129998   |
| LLA      |     187 |  3351 | 1989.54 |     1930 |  1352 | 330.59 | 109292   |
| LPL      |     786 |  3363 | 1893.44 |     1856 |  1150 | 313.9  |  98536.1 |
| PCS      |     271 |  3047 | 1858.03 |     1809 |  1115 | 342.04 | 116989   |
| VCS      |     323 |  2910 | 1800.96 |     1769 |  1071 | 288.26 |  83092.6 |

---

## Assessment of Missingness:
We believe that there is a column in the data set that is Not Missing At Random, which is monster kills own at jungle. This is because although this stat may seem completely random, the empty data can be explained by where the map takes place. If a map in league does not have a jungle map, then there cannot be any monster kills, which is why that data is null for certain games. However, since that certain data is not on the csv file, this cannot be concluded.

For our analysis on choosing two variables, we chose to have our two columns that do not depend on each other to be double kills for missing and wpm. Having double kills present or not does not exactly correlate with the wpm in competitive matches as the missingness in double kills is most likely due to the game being partially completed. After manually looking at the data, we concluded that double kills is most likely null for partial games since the game has not been officially a full game for the stats to be concluded.

#### Results of Permutation
For our permutation tests, we chose to do columns 'doublekills' and compare that with 'wpm' and 'gamelength'. By looking at the data, we are able to reasonably assume that the reason why doublekills are empty for some games is because they were not reported since the game has not completed, which explained why there are missing stats that correlate to the game being partial on the dataset. This would also mean that incomplete games would have a smaller gamelength, which also means that they will have a missing value in double kills. Therefore, doublekills and gamelength are dependent on each other. As seen in the graph below. We also got a p value of 0.0, which is extremely low and proves that those twocolumns are dependent on each other. As seen in the graph below gamelength of complete and missing doublekills are not identically distributed.
<p><iframe src="plot6.html" width=800 height=600 frameBorder=0></iframe></p>

We assume that 'doublekills' and 'wpm' do not depend on each other because wpm means wards per minute, as they do not depend on whatever or not a game is completed or not since wards per minute is instead determined on how the game is played by the players. As seen in the graph below, the values of wpm of complete and missing doublekills are not identically distributed.
<p><iframe src="plot7.html" width=800 height=600 frameBorder=0></iframe></p>

---

## Hypothesis Testing:
- Null Hypothesis: There is no significant difference in the average game length between all of the tier 1 leagues in League of Legends.
- Alternative hypothesis: There are significant differences in the average game lengths between tier 1 leagues in League of Legends.
- Test statistic: T-test
- Significance level: 0.05/36, using alpha bernouli since there are 9 leagues in tier 1 and a total of 36 comparisons for all of the leagues
- The P-value between every combination of the leagues is as follows:
  - The P value between CBLOL and LCK is 0.09463990461494619
  - The P value between CBLOL and LCS is 0.7876156683770301
  - The P value between CBLOL and LEC is 0.5373527716345259
  - The P value between CBLOL and LJL is 0.10207328430808504
  - The P value between CBLOL and LLA is 0.6261142149262305
  - The P value between CBLOL and LPL is 0.0005256706367859629
  - The P value between CBLOL and PCS is 9.005130506488931e-05
  - The P value between CBLOL and VCS is 4.375151567768843e-11
  - The P value between LCK and LCS is 0.1315083620379078
  - The P value between LCK and LEC is 0.3472804909787468
  - The P value between LCK and LJL is 0.0009890558218275361
  - The P value between LCK and LLA is 0.3161959546967639
  - The P value between LCK and LPL is 9.314774760529871e-11
  - The P value between LCK and PCS is 2.992591664215375e-09
  - The P value between LCK and VCS is 6.694916135134773e-19
  - The P value between LCS and LEC is 0.6912287326362201
  - The P value between LCS and LJL is 0.0490400404839303
  - The P value between LCS and LLA is 0.7936396948845161
  - The P value between LCS and LPL is 3.992102102090342e-05
  - The P value between LCS and PCS is 1.0572958670128944e-05
  - The P value between LCS and VCS is 5.076060868498343e-13
  - The P value between LEC and LJL is 0.03522194308818198
  - The P value between LEC and LLA is 0.9126692988401927
  - The P value between LEC and LPL is 3.2366223946643715e-05
  - The P value between LEC and PCS is 1.599648873927649e-05
  - The P value between LEC and VCS is 5.662536887803942e-12
  - The P value between LJL and LLA is 0.051695087953736514
  - The P value between LJL and LPL is 0.2577316630510385
  - The P value between LJL and PCS is 0.047206801281997945
  - The P value between LJL and VCS is 2.060568938709088e-05
  - The P value between LLA and LPL is 0.0002075167042443045
  - The P value between LLA and PCS is 4.897368171899932e-05
  - The P value between LLA and VCS is 4.2819772152884424e-11
  - The P value between LPL and PCS is 0.11803774648906282
  - The P value between LPL and VCS is 5.6061553426685654e-06
  - The P value between PCS and VCS is 0.027700142589951404           
  - The T test is a good choice for this question because we are comparing the means of groups. We chose 0.05/36 by using alpha bernouli as our significant level due to there being a total of 36 comparisons needed. This is because we don’t have that much evidence to reject this null hypothesis. 
- After running our hyothesis test, We see that there are significant differences in average game duration between certain leagues.

---
