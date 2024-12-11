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
In order to compress the amount of data present in the raw dataframe, I only took relevant columns which I would use for analysis. These include: league, position, visionscore, gamelength, result, total cs, csat15, csat25, killsat25, assistsat25, deathsat25. Additionally, I chose to analyze data from the LCK, specifically the support role. In the original raw dataframe, there were 150180 rows and 161 columns. After reduction, there were 934 rows and 12 columns. 
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

Support DataFrame

<br>

| league   | position   |   visionscore |   gamelength |   result |   total cs |   csat15 |   csat25 |   killsat25 |   assistsat25 |   deathsat25 | is_25   |
|:---------|:-----------|--------------:|-------------:|---------:|-----------:|---------:|---------:|------------:|--------------:|-------------:|:--------|
| LCK      | sup        |           115 |         2195 |        0 |         36 |       11 |       22 |           1 |             3 |            0 | True    |
| LCK      | sup        |           108 |         2195 |        1 |         17 |        4 |       12 |           0 |             2 |            1 | True    |
| LCK      | sup        |            82 |         2070 |        0 |         40 |       31 |       34 |           1 |             1 |            1 | True    |
| LCK      | sup        |           101 |         2070 |        1 |         41 |       21 |       35 |           0 |             1 |            0 | True    |
| LCK      | sup        |           112 |         2233 |        1 |         30 |        9 |       21 |           1 |             4 |            2 | True    |

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

<iframe
    src="plots/plot_3.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

<iframe
    src="plots/plot_4.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

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



