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

The prediction problem involves predicting the vision score (visionscore) of a support player at the end of a game. This is a regression problem since the target variable, visionscore, is a continuous numerical value.
<br>
<br>
***Response Variable***
<br>
<br>
Since this is the metric we are interested in forecasting, the response variable is the final vision score. In League of Legends, the vision score is crucial since it shows how the player contributes to map awareness and strategic control, both of which can affect the game's outcome.
<br>
<br>
***Evaluation Metric***
<br>
<br>
Mean Squared Error (MSE) or Mean Absolute Error (MAE) could be used as the evaluation metric to gauge the model's performance. Because they concentrate on the model's capacity to forecast a continuous numerical variable, these measures are suitable. Because MAE displays the average error in the same units as the goal variable (vision score), it is easier to read. Since metrics like accuracy and F1-score are better suited for classification jobs rather than regression, I went with MAE instead.
<br>
<br>
***Information at the Time of Prediction***
<br>
<br>
Certain variables, such the game's duration, outcome (win or lose), and whether it lasted more than 25 minutes, would be available to us at the time of projection. Only in-game features available during the match should be used for prediction, as we would not have access to post-game statistics or future game outcomes.
<br>
<br>
***Justification for Feature Selection***
<br>
<br>
Because they offer information that may affect the eyesight score during a match, we are using features such game length, game outcome, and if the game lasts more than 25 minutes. Other components should be left out since they wouldn't be accessible during prediction time, like final results or statistics after a game.

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

***Model Description***
<br>
<br>
The model used in this analysis is a Linear Regression model. It is trained to predict the vision score (visionscore) of a support player at the end of a game based on three features:

<p><strong>killsat25</strong> (Quantitative): The number of kills a support player has at 25 minutes.</p>
<p><strong>assistsat25</strong> (Quantitative): The number of assists a support player has at 25 minutes.</p>
<p><strong>is_25</strong> (Nominal): A binary feature indicating whether the game lasted more than 25 minutes.</p>

<br>
<br>
***Data Preprocessing and Encoding***
<br>
<br>
Numerical Features: Killsat25 and Assistsat25 are numerical (quantitative) characteristics that are scaled using StandardScaler to guarantee that their scales are comparable for the model after being preprocessed using SimpleImputer to fill in any missing values with the mean.
<br>
<br>
Categorical Features: OneHotEncoder is used to encode the is_25 feature, which is categorical (nominal) and produces a binary feature (whether or not the game lasted more than 25 minutes). In order to prevent multicollinearity, we exclude the first category.
<br>
<br>
To guarantee correct handling of the data during training and testing, these preprocessing processes are carried out inside a ColumnTransformer, and both preprocessing and the model training phases are incorporated into a Pipeline.
<br>
<br>
***Model Performance***

<iframe
    src="plots/plot_12.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>

performance of the model was evaluated using Mean Squared Error (MSE), which measures the average squared difference between the actual and predicted vision scores. The baseline model's MSE is 930.73.
<br>
<br>
***Is the Model "Good"?***
<br>
<br>
An MSE of 930.73 indicates that the model's predictions have a significant amount of error, even though the model has attained an MSE value, which helps evaluate its prediction accuracy. The use case in question and the anticipated level of prediction accuracy determine whether this model is "good" or not. Additional enhancements to this model might include investigating more intricate models (such decision trees or random forests) or adding features that could more accurately predict vision score, such as player champion type or in-game events that impact vision score. Additionally, assessing additional metrics like R-squared may offer additional understanding of the model's functionality.

# Final Model

***Features Added***
<ul>
    <li><strong>creep_score_per_minute</strong>: This feature calculates the number of creeps (minions and monsters) killed per minute. This is a good feature for the prediction task because it reflects a player's ability to manage the map and participate in key objectives, which influences their overall contribution to the game and their vision score.</li>
    <li><strong>cumulative_kda_at_25</strong>: This feature represents a player's cumulative KDA (Kills + Assists - Deaths) at 25 minutes. It helps measure a player’s performance, indicating their impact in terms of kills and deaths, which is relevant to the vision score.</li>
</ul>

***Modeling Algorithm***

<p>I used a <strong>RandomForestRegressor</strong> for predicting the vision score. Random forests are a versatile and powerful ensemble learning method, which works well for regression tasks with multiple features, such as the ones in this dataset. They can capture complex relationships and interactions between features.</p>

***Hyperparameters***

<ul>
    <li><strong>n_estimators</strong>: The number of trees in the forest. The best performing values were 100 and 200.</li>
    <li><strong>max_depth</strong>: The maximum depth of the tree. The optimal values were 10, 15, and 20.</li>
    <li><strong>min_samples_split</strong>: The minimum number of samples required to split an internal node. Values of 2 and 5 were tested.</li>
    <li><strong>min_samples_leaf</strong>: The minimum number of samples required to be at a leaf node. The values tested were 1 and 2.</li>
</ul>

***Hyperparameter Selection***
<p>Hyperparameters were selected using <strong>GridSearchCV</strong> with cross-validation. This method tested all combinations of the hyperparameter grid and selected the best combination based on model performance.</p>

***Model Performance***

<p>The final model achieved a Mean Squared Error (MSE) of <strong>263.57</strong>, which is a significant improvement over the baseline model's MSE of <strong>930.73</strong>. This indicates that the RandomForest model, after fine-tuning, was able to predict the vision score much more accurately.</p>

***Visualization***

<p>Below is a scatter plot of the actual vs predicted vision scores, with a red dashed line representing the ideal prediction (where actual equals predicted). This plot visually demonstrates the accuracy of the final model:</p>

<iframe
    src="plots/plot_13.html"
    width="800"
    height="600"
    frameborder="0"
></iframe>



# Fairness Analysis

<p><strong>Choice of Groups:</strong></p>
<p><strong>Group X (Losses):</strong> This group includes all the instances where the result is a loss (0). It is selected from the dataset using <code>support_data['result'] == 0</code>.</p>
<p><strong>Group Y (Wins):</strong> This group includes all the instances where the result is a win (1). It is selected from the dataset using <code>support_data['result'] == 1</code>.</p>

<p><strong>Evaluation Metric:</strong></p>
<p>The evaluation metric used is the <strong>Mean Squared Error (MSE)</strong>, which is a common metric for regression tasks. It measures the average squared difference between the predicted and actual values. Lower MSE indicates better model performance.</p>

<p><strong>Null and Alternative Hypotheses:</strong></p>
<ul>
    <li><strong>Null Hypothesis (H₀):</strong> There is no significant difference in MSE between losses and wins.</li>
    <li><strong>Alternative Hypothesis (H₁):</strong> There is a significant difference in MSE between losses and wins.</li>
</ul>

<p><strong>Test Statistic:</strong></p>
<p>The test statistic is the difference in MSE between the losses group (Group X) and the wins group (Group Y). We perform a permutation test to assess the statistical significance of this difference.</p>

<p><strong>Significance Level:</strong></p>
<p>The significance level is set at 0.05, meaning we will reject the null hypothesis if the p-value is less than 0.05.</p>

<p><strong>Results:</strong></p>
<ul>
    <li><strong>MSE for Losses:</strong> 88.38</li>
    <li><strong>MSE for Wins:</strong> 121.28</li>
    <li><strong>P-value from Permutation Test:</strong> 1.0</li>
</ul>

<p><strong>Conclusion:</strong></p>
<p>Since the p-value is 1.0, which is greater than 0.05, we fail to reject the null hypothesis. Therefore, we conclude that there is no significant difference in the MSE between the losses and wins groups in our dataset.</p>
