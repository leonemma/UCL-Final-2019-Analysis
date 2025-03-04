# Champions League Final 2019 Analysis

## Authors

- [@leonemma](https://github.com/leonemma)
- The source code for this project is available [here](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/Football%20Data%20Analysis.ipynb).

## Contents  
- [Introduction](#Introduction)
- [Installation](#Installation)
- [Data](#Data)
- [Key Questions](#Key-Questions)
- [Game Analysis](#Game-Analysis)
  - [Lineups-Heatmaps](#Lineups)
  - [Expected Goals](#Expected-Goals)
  - [Possession](#Possession)
  - [Passing Networks](#Passing-Networks)
  - [Pressure Heatmaps](#Pressure-Heatmaps)
  - [Total Shots, Passes & Dribbles](#Shots-Passes-Dribbles)
  - [Dashboard](#Players's-Contribution)
    
## Introduction

Welcome to the UEFA Champions League Final 2019 Data Analysis project! In this analysis, we dive deep into an epic battle between Liverpool and Tottenham Hotspur, exploring key statistics, tactical insights and player performances, that shaped the outcome of one of football's most important matches of the season.

Key Findings:
- Team Statistics: We examined various team statistics, including shots, expected goals (xG), passes and other key performance indicators, providing a comprehensive overview of each team's performance on the pitch.

- Visualizations: We utilized the mplsoccer library to create visualizations such as shot maps and passing networks and heatmaps, providing intuitive representations of match dynamics and player interactions.

- Dashboard: Additionally, we developed an  dashboard using Tableau, offering detailed statistics and insights into the performance of each player during the UEFA Champions League Final.
  
## Installation

1. Python: Set up a Python environment suitable for running the analysis scripts or Jupyter notebooks. You may use Anaconda or create a virtual environment.

2. Dependencies: Make sure you have the required Python libraries installed. In this project we will use data and a lot of functions from the mplsoccer library. You can install it using pip:
     ```python
     pip install mplsoccer 
     ```
     - pandas
     - numpy
     - matplotlib
     - scipy
     - seaborn

3. Power BI 
- Power BI Desktop: Download and install Power BI Desktop from the official [website](https://powerbi.microsoft.com/en-us/desktop/)
- Open Dashboards: After downloading the [dashboard](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/UCL%20Final%202019.pbix) file, you can open it using Power BI Desktop.

4. Tableau Dashboard:
 - Utilized Tableau for insightful data visualization and analysis.
 - To access the Tableau dashboard, click [here](https://public.tableau.com/app/profile/leonidas.emmmanouilidis/viz/UCLFinal2019_17133834605920/Dashboard1)
   
## Data   
This analysis utilizes the `mplsoccer` library to load and analyze football (soccer) event data. The dataset used is sourced from **StatsBomb**, an open-source football analytics provider known for its detailed event data.

The data in this project is parsed using `mplsoccer`'s `Sbopen` parser, which supports **StatsBomb JSON event data**. StatsBomb provides extensive match event data, including passes, shots, tackles, and other key football actions.

The following code snippet demonstrates how the data is loaded:

```python
from mplsoccer import Sbopen, VerticalPitch, Pitch, create_transparent_cmap, FontManager, arrowhead_marker

# Initialize parser
parser = Sbopen()

# Load competition, match, lineup, and event data
df_competition = parser.competition()
df_match = parser.match(competition_id=16, season_id=4)
df_lineup = parser.lineup(22912)
df_event, df_related, df_freeze, df_tactics = parser.event(22912)
```

### Understanding the Data
- **`competition()`**: Retrieves details about different competitions.
- **`match(competition_id, season_id)`**: Fetches match details for a given competition and season.
- **`lineup(match_id)`**: Provides lineup details for a specific match.
- **`event(match_id)`**: Retrieves in-game event data, including passes, shots, and tackles.

StatsBomb data is widely used in football analytics due to its high level of detail and accuracy. Unlike proprietary sources such as **Opta** or **Wyscout**, StatsBomb offers open-source datasets, making it ideal for analysis and visualization.

For further details, refer to the official [StatsBomb Open Data repository](https://github.com/statsbomb/open-data).


1.  The data for this analysis was obtained using the __mplsoccer__ library, which provides functionalities for accessing football match data. Here's a breakdown of the retrieval process:
```python
from mplsoccer import Sbopen, VerticalPitch, Pitch, create_transparent_cmap, FontManager, arrowhead_marker
```
2.  Data Retrieval: We used the parser module from the mplsoccer library to retrieve specific data related to the UEFA Champions League Final 2019.
```python
df_competition = parser.competition()
df_match = parser.match(competition_id=16, season_id=4)
df_lineup = parser.lineup(22912)
df_event, df_related, df_freeze, df_tactics = parser.event(22912)
```
3.  Dataframe Selection: Among the retrieved dataframes, we primarily utilized __df_event__ for our analysis, as it contained the relevant match event data.

## Key-Questions  

1. How did the expected goals (xG) change throughout the match, and what moments influenced these changes?
2. How did the distribution of possession in different areas of the pitch?
3. Which players were most involved in the passing buildup?
4. Which passing combinations were most frequently used?
5. Where did each team apply the most pressure on their opponents?
6. Which players had the most significant impact on the game based on the overall contribution metrics?


## Game-Analysis  
  ### Match Score
  In the UEFA Champions League final of 2019, Liverpool achieved a victory against Tottenham Hotspur with a score of __2-0__. The match showcased Liverpool's effective defense and  finishing in the attacking field, securing their sixth European title. 

  ### Lineups
  
  The following visualization presents the lineups for both teams combined by individual heatmaps showcasing the on-field activity of each starting player. A heatmap serves as a graphical representation of a player's involvement and actions in ball-related activities on the field, throughout the game. This visualization offers valuable insights into each player's performance and tactical contributions during the match.

  
   ![lineups_plot](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/lineups_heatmaps.png)



  ### Expected-Goals
  
  Expected Goals (xG) in football evaluates the quality of scoring opportunities, offering deeper insights beyond traditional statistics like goals scored, by assessing the likelihood of scoring based on various factors.  
  
   ![xG](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/sum_xG.png)

  By visualizing the xG values on a minute-by-minute basis, we can analyze the scoring opportunities created by both teams and track the __momentum__ shifts during the match. Here's a line chart by use of Power BI showcasing the progression of scoring opportunities for both teams during the game.  
 
   ![xG_sum](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/sum_xg_final.PNG)  

   It's important to note that Liverpool scored at the beginning of the game (1') with a penalty. That's why the xG at the start of the game is at 0.78 xG. The line chart above showcases that neither team had a scoring chance that was greater than 0.2 xG after the Liverpool's penalty at the beginning of the game. 

  ### Possession  

  The following pie plot showcase the possession distribution during the game. Overall, the possession distribution indicates that Tottenham had an advantage in having the ball. However, it's necessary to take into account more metrics in order to interpretate the game result.   

  ![Possession](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/Possession.png)
  
  ### Passing-Networks  
  A passing network in football refers to a visual representation or analysis of the passing interactions between players on a team during a match. Passing networks can provide insights into the patterns of play, teamwork dynamics, and strategies employed by a team during a match. They can reveal which players are involved in the build-up of play and the effectiveness of passing connections between different areas of the pitch.   

![Liverpool_Pass_Netw](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/Liverpool_Passing_Network.png)    

In a passing network, the thickness of a line between two players represents the frequency or volume of passes exchanged between them. When the line between two players, such as the left-back (LB) and the left-winger (LW) as shown above, is thick, it signifies a high number of passes between them. This indicates that those players are heavily involved in passing exchanges, often playing a significant role in the team's build-up play or in circulating possession from deep positions. Additionally, the size of a player's node corresponds to the frequency of ball touches he had highligting his involvement in the team's build-up play.

![Tottenham_Pass_Netw](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/Tottenham%20PassNetw.png)  

  ### Pressure-Heatmaps  
  A pressure heatmap in football visualizes the intensity and location of defensive pressure exerted by a team on their opponents during a match. It provides insights into how effectively a team applies pressure on their opponents to disrupt their play, regain possession, or force them into making mistakes.  

  - Liverpool's heatmap highlights the high pressing strategy of the team. Liverpool aimed to win back possession of the ball quickly by putting intense pressure on the opponent's players just before Tottenham enter the attacking half.
   
 ![Liverpool_Heatmap](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/final_liverpool.png)

 - On the other hand, it's obvious that Tottenham chose to pay attention to Liverpool's left back (Robertson) and right winger (Salah) , who had a solid game as we will see later, by putting pressure on them.
  
 ![Tottenham_Heatmap](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/final_tottenham.png)

  ## Shots-Passes-Dribbles 
  ### Total Shots:
  The following donut charts present the total shots of each team including the shots that was on target.

   ![total_shots](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/total_shots.png)  

  - Liverpool had 3/14 shots on target, but still achieved two goals.
  - Tottenham had way better aim, succeeding 8 shots on target out of 16 total shots. However, Spurs were unable to score a goal.


  #### Shots Map   
  
  In the following shot maps we can see the locations of shots taken by Liverpool's and Tottenham's players during the match. The bigger the marker is the greater the expected goal of the corresponding shot. It's obvious that the biggest chance for Liverpool based on the xG was the penalty that had at the beginning of the game (1'), when Salah scored (0.78 xG).  Although Tottenham attempted to score from outside Liverpool's penalty area 8 times, they also created some promising chances within the box, without succeeding.

  ![shot_maps](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/shots_maps_final_see.png)    


  ### Total Passes/Accuracy(%)
  Tottenham was more dominant in ball traffic, making more passes overall and significantly greater passing accuracy (79.3%) compared to Liverpool (62.0%), showcasing their control and precision in possession during the match.  


   ![total_passes](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/total_passes.png)  

 #### Passing Arrows Map  
 Passing arrows maps are powerful visual tools that help teams and analysts evaluate passing dynamics, identify strengths and weaknesses, and make informed decisions to optimize their 
 tactical strategies.    

 - The passing arrows map below highlights Liverpool's desire to attack and build up from the left side, aiming Robertson and Mane. Successful passes are more frequent from this area, indicating a focused effort to build up from the left flank. Liverpool's had also difficulties in feeding players in opponent's box, that's why the number of successful passes in Tottenham's penalty area is minimal.

 ![Liverpool_pass_arrow](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/liverpool_arrow.png)   

  
 - On the other hand, Tottenham had a greater number of passes but it's obvious that the majority of them were in their own half. Although, the passes in the Liverpool's box is significantly decreased, as it is shown below, it's significantly greater than Liverpool's successful attempts.
   
 ![Tottenham_pass_arrow](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/Tottenham_Arrows.png)  


  ### Total Dribbles
  The following plot focuses on the dribbles each team attempted during the game, including the successful attempts.  

   ![total_dribbles](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/total_dribbles2.png)

  Liverpool completed 2 successful dribbles out of 6 attempts, while Tottenham achieved 4 successful dribbles out of 9 attempts, achieving a higher success rate during the match. 



  ### Players's-Contribution  

  Finally, we've developed a Tableau dashboard showcasing the distribution of diverse football metrics attributed to players. These include statistics like shots taken, aerial duels won, and possession indicators such as passes, ball receipts, and carries. In addition, the table in the top right corner displays players' shots, detailing each shot's outcome and its corresponding expected goals (xG) value.  

  ![dashboard](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/Dashboard%201.png) 


#### Additional remarkable insights from the game:
  - Origi scored the second goal with xG value of 0.08 ! 
  - Salah had the most scoring attempts (6 shots) during the game for both teams and the most ball receipts (52) for Liverpool. Sadio Mane is second in the ball receipts with 45 for Liverpool.
  - Robertson is the player with the most passes (54) and carries (29) for Liverpool with Trent Alexanter Arnold in the second place in passes with 47, highlighting Liverpool's strategic emphasis on using their wide players to build up and create scoring opportunities.
  - We confirm Tottenham's possession dominance, since the defenders dominated in passing, ball receipts and carries too. Spurs's goalkeeper (Lloris) participated in team's build up, showcasing the importance of a modern goalkeeper to have  really good skills with the ball.
  - Lloris received the ball 42 times, indicating that Tottenham's players passed to him frequently. This reflects Liverpool's intense pressure in their attacking third    

  
                     
  
