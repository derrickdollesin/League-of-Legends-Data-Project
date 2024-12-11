# Introduction
<br>
League of Legends (LoL) is a multiplayer online battle arena (MOBA) game developed and published by Riot Games. Two teams of five players compete to defend their base while demolishing the Nexus of the opposing team. Players take control of a variety of characters known as "champions", each with unique playstyles and powers, to achieve objectives such as defeating rival champions, destroying turrets, and capturing neutral creatures.
<br>
<br>
The professional data set that I will be working with was created by Oracle's Elixir. Match data from professional LOL esports gaming matches throughout 2022 is recorded in the dataset. By collecting significant gaming data and outcomes from a selection of LOL matches, this dataset offers a multitude of information for understanding player behavior, team dynamics, and match outcomes. Among the features it provides are in-game statistics, team strategies, individual player performance, and overall match dynamics.
<br>
<br>
In League of Legends (LOL), the "***visionscore***" has to do with "wards" placed by players around the map. These "wards" grant vision to areas of the map otherwise hidden to player view. Controlling more vision of the map allows for players to track enemy movement and obtain positional advantages against their enemies. "***Creep score***" is the number of minions and jungle monsters killed by a champion. These kills generate gold for players which allow them to get ahead of their opponents through bought items.
<br>
<br>
The central question I am interested in is: ***How much of an impact does the vision and creep score for support players have on the other gaming metrics in the LCK?*** 
<br>
<br>
In the original dataset there are around 150180 rows. The rows which I decided to keep to analyze include: league, position, visionscore, gamelength, result, total cs, csat15, csat25, killsat25, assistsat25, deathsat25.
<br>
<br>
<ul>
    <li><b>League</b>: Competitive league which data was pulled from.</li>
    <li><b>Position</b>: Role played by players.</li>
    <li><b>Visionscore</b>: Effectiveness of vision placement.</li>
    <li><b>Gamelength</b>: Duration of the match in minutes.</li>
    <li><b>Result</b>: Win or loss (coded as 1 or 0).</li>
    <li><b>Total CS</b>: Total minion and monster kills.</li>
    <li><b>CS at 15/25</b>: Creep score at 15 and 25 minutes.</li>
    <li><b>Kills at 25</b>: Total kills at 25 minutes.</li>
    <li><b>Deaths at 25</b>: Total Deaths at 25 minutes.</li>
    <li><b>Assists at 25</b>: Total Assists at 25 minutes.</li>
    <li><b>is_25</b>: Boolean true or false if the game lasted 25 minutes.</li>
</ul>

# Data Cleaning and Exploratory Data Analysis
<br>
The goal of the data cleaning procedure was to improve the dataset so that it could be utilized to examine LCK league support players. To ensure that the analysis was league-specific, the data was first filtered to only contain rows with the league set to 'LCK'. To facilitate time-based operations, the date column was transformed into a datetime format, and rows with incomplete data (designated by datacompleteness) were eliminated. To make the dataset more manageable, the url column—which had no bearing on the analysis—was removed. By filtering for the'sup' position, the focus was then reduced to players who were supporting roles. To make subgroup comparisons easier, a new column, is_25, was introduced to indicate whether the game lasted more than 25 minutes. Lastly, the dataset's complexity was decreased by retaining only pertinent columns (such as visionscore, gamelength, outcome, csat25, etc.).
<br>
<br>
These procedures made sure the dataset was precise, comprehensive, and concentrated on the relevant elements of gaming. The data was made more digestible and suitable for in-depth research by separating the LCK league, concentrating on support players, and include crucial indicators for game duration. Now that the dataset had been cleaned, it could be examined using statistical tests and visualizations to reveal how various elements, such game length and result, affected support players' performance in the LCK competition.
<br>
<br>
Support DataFrame

| league   | position   |   visionscore |   gamelength |   result |   total cs |   csat15 |   csat25 |   killsat25 |   assistsat25 |   deathsat25 | is_25   |
|:---------|:-----------|--------------:|-------------:|---------:|-----------:|---------:|---------:|------------:|--------------:|-------------:|:--------|
| LCK      | sup        |           115 |         2195 |        0 |         36 |       11 |       22 |           1 |             3 |            0 | True    |
| LCK      | sup        |           108 |         2195 |        1 |         17 |        4 |       12 |           0 |             2 |            1 | True    |
| LCK      | sup        |            82 |         2070 |        0 |         40 |       31 |       34 |           1 |             1 |            1 | True    |
| LCK      | sup        |           101 |         2070 |        1 |         41 |       21 |       35 |           0 |             1 |            0 | True    |
| LCK      | sup        |           112 |         2233 |        1 |         30 |        9 |       21 |           1 |             4 |            2 | True    |

<br>
<br>
The distribution of Creep Score at 25 minutes (csat25) for LCK league support players is displayed in the first plot. To show the spread and possible outliers in the data, a box plot has been added above the histogram, which depicts the distribution as a whole. Since support players usually concentrate on map control and vision rather than farming, it is not surprising that most of them have lower csat25s.
<br>
<br>
In the second, the csat25 distribution is compared according to whether the game lasted longer than twenty-five minutes (is_25). This overlay histogram shows that longer games typically result in greater creep scores, indicating that players have more time to farm throughout longer game durations. But the distributions' overlap suggests that there are other factors besides game length.
<br>
<br>
<iframe
    src="plots/plot_1.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

<iframe
    src="plots/plot_2.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>
<br>
<br>
Color-coded by game outcome (result), the scatter figure shows the correlation between game time (gamelength) and creep score at 25 minutes (csat25). We can see from the plot that the csat25 tends to rise with game length, indicating greater farming chances for participants. According to the data, support players who win games typically have a somewhat better csat25 than those who lose. Although the correlation is weak, suggesting that other factors also affect their success, this pattern implies that longer games and victory may offer support players more opportunities to accumulate farm.
<br>
<br>
<iframe
    src="plots/plot_5.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>
<br>
<br>
The table below presents the aggregate statistics for Creep Score at 25 minutes (csat25), grouped by game outcome (result, where 1 indicates a win and 0 indicates a loss). The statistics include the mean, median, standard deviation, and count for each outcome.

|    mean |   median |     std |   count |
|--------:|---------:|--------:|--------:|
| 32.8079 |       31 | 29.8454 |     453 |
| 32.8874 |       31 | 32.0591 |     453 |

Support players in winning games (when result = 1) typically have a higher average Creep Score at 25 minutes (mean = 32.8874) than those in losing games (mean = 32.8079), according to this table. Significant variation in Creep Scores within each group is indicated by the comparatively large standard deviations for both outcomes. This implies that individual performance still varies greatly even when winning games are linked to greater Creep Scores at 25 minutes. The table highlights the possible connection between support players' farming performance and game outcomes.

# Assessment of Missingness

I draw the conclusion that the csat25 column in the dataset is missing in an NMAR (Not Missing at Random) manner based on the permutation test findings. The p-value of 0.0 indicates a strong rejection of the null hypothesis, which held that the missingness in csat25 was independent of gamelength. The permutation test assessed whether the missingness of csat25 is connected to gamelength. This supports the notion that missingness varies with game length by showing that missing values in csat25 are more likely to occur in games of a particular length.
<br>
<br>
There is a significant correlation between the two variables, as evidenced by the observed difference in mean gamelength of 729.36 between the missing and non-missing csat25 values. The idea that longer or shorter games may be linked to missing data in csat25 is supported by this finding. This could be because of a number of variables, including incomplete game recordings or missing data for specific game lengths.
<br>
<br>
More information could be helpful to better understand the nature of this missingness and possibly turn it into MAR (Missing at Random). For instance, the absence of csat25 in some games may be explained by game metadata like match type, player behavior, or other in-game occurrences. It would be possible to treat missingness more accurately and get a better understanding of the mechanisms underlying the missing data if these variables were gathered.
<br>
<br>
***Permutation Test Plot***
<iframe
    src="plots/plot_6.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>
<br>
<br>
The distribution of the mean differences in gamelength for missing and non-missing csat25 values from 1,000 permutations is displayed in the histogram below. The observed difference in means, 729.36, is shown by the red dashed line. The conclusion that the missingness in csat25 is NMAR is supported by the p-value of 0.0, which shows that the observed difference is significantly different from the simulated differences.

# Hypothesis Testing

<h2>Hypotheses:</h2>
<p><strong>Null Hypothesis (H₀):</strong> Higher csat15 score does not result in a win.</p>
<p><strong>Alternative Hypothesis (H₁):</strong> Higher csat15 score results in a win.</p>

In order to compare the means of csat15 between games that ended in a win (result = 1) and games that ended in a loss (result = 0), I used a two-sample t-test. Since the assumption of unequal variances was taken into consideration and we are comparing the means of two independent groups, this test is appropriate (thus, employing Welch's t-test). A significance threshold of 0.05 was established.

<h2>Results:</h2>
<p><strong>T-statistic:</strong> 5.80</p>
<p><strong>P-value:</strong> 8.99e-09</p>

<br>
<br>
We reject the null hypothesis in favor of the alternative hypothesis since the p-value is less than 0.05. This indicates that there is enough data to imply that a higher csat15 score corresponds to a higher chance of winning.
<br>
<br>
Conclusion: Better creep scores early in the game can help a team win, as the t-test result confirms that higher csat15 scores are substantially connected with winning games. It is crucial to remember that other factors may also affect game outcomes, therefore this does not prove a cause-and-effect relationship.
<br>
<br>
Visualization: The distribution of csat15 scores for wins and losses is displayed in the histogram below. The overlay shows that, in comparison to losing games, winning games typically have better csat15 scores.

<iframe
    src="plots/plot_7.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

# Framing a Prediction Problem

<iframe
    src="plots/plot_8.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

<iframe
    src="plots/plot_9.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

<iframe
    src="plots/plot_10.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

<iframe
    src="plots/plot_11.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

# Baseline Model

<iframe
    src="plots/plot_12.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

# Final Model

<iframe
    src="plots/plot_13.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>



