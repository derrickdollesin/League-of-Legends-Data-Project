# Introduction
<br>
League of Legends (LoL) is a multiplayer online battle arena (MOBA) game developed and published by Riot Games. Two teams of five players compete to defend their base while demolishing the Nexus of the opposing team. Players take control of a variety of characters known as "champions", each with unique playstyles and powers, to achieve objectives such as defeating rival champions, destroying turrets, and capturing neutral creatures.
<br>
<br>
The professional data set that I will be working with was created by Oracle's Elixir. Match data from professional LOL esports gaming matches throughout 2022 is recorded in the dataset. By collecting significant gaming data and outcomes from a selection of LOL matches, this dataset offers a multitude of information for understanding player behavior, team dynamics, and match outcomes. Among the features it provides are in-game statistics, team strategies, individual player performance, and overall match dynamics.
<br>
<br>
In League of Legends (LOL), the "***visionscore***" has to do with "wards" placed by players around the map. These "wards" grant vision to areas of the map otherwise hidden to player view. Controlling more vision of the map allows for players to track enemy movement and obtain positional advantages against their enemies. "***Creep score***" is the number of minions and jungle monsters killed by a champion. These kills generate gold for players which allow them to get ahead of their opponents through bought items.|
<br>
<br>
The central question I am interested in is: ***How much of an impact does the vision and creep score statline have on the other gaming metrics in the dataset?*** 

# Data Cleaning and Exploratory Data Analysis

<h5>Support DataFrame</h5>

| ESPORTSTMNT01_2690705 | complete           | LCK      |   2022 | Spring  |          0 | 2022-01-12 10:07:10 |      1 |   12.01 |               5 | Blue   | sup        | Keria        | oe:player:db79ce6ad35451c938fbe2995dabd37 | T1           | oe:team:ce499dea30cfce118f4fe85da0227e8 | Karma      | Lee Sin  | Ryze    | Viktor       | LeBlanc | Graves  |     nan |     nan |     nan |     nan |     nan |         2233 |        1 |       1 |        3 |         9 |          12 |            7 |             0 |             0 |             0 |            0 |            1 |                0 |                  1 |                  0 |     0.3224 | 0.5105 |           nan |       nan |           nan |               nan |                   nan |         nan |         nan |      nan |      nan |         nan |        nan |                      nan |      nan |          nan |           nan |       nan |           nan |          nan |              nan |          nan |        0 |            0 |          nan |      nan |          nan |             nan |                  nan |            nan |                nan |            0 |                0 |               14309 | 384.478 |     0.192514  |                327.595 |                    230.112 |            66 | 1.7734 |            13 | 0.3493 |                   21 |           112 | 3.0094 |        9131 |         4301 |     115.567  |         0.101664  |        8775 |    nan |   nan |         30 |            29 |              1 |                     nan |                       nan | 0.8061 |       2516 |     2230 |        5 |           2352 |         3141 |            5 |            164 |         -911 |            0 |           0 |             1 |            1 |               0 |                 1 |                0 |       4081 |     4079 |        9 |           3355 |         4423 |            8 |            726 |         -344 |            1 |           1 |             2 |            1 |               0 |                 1 |                2 |       5030 |     5205 |       15 |           4874 |         6050 |           18 |            156 |         -845 |           -3 |           1 |             2 |            1 |               1 |                 1 |                2 |       6183 |     7256 |       21 |           5922 |         7665 |           31 |            261 |         -409 |          -10 |           1 |             4 |            2 |               1 |                 1 |                2 | True    |


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



