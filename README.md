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

# Assessment of Missingness

<iframe
    src="plots/plot_6.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

# Hypothesis Testing

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



