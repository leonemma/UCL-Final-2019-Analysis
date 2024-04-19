# Champions League Final 2019 Analysis
Dive into match statistics, player performances and tactical insights

## Authors

- [@leonemma](https://github.com/leonemma)
- The source code for this project is available [here](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/Football%20Data%20Analysis.ipynb).

## Contents  
- [Introduction](#Introduction)
- [Installation](#Installation)
- [Data](#Data)
- [Game Analysis](#Game-Analysis)

## Introduction

Welcome to the UEFA Champions League Final 2019 Data Analysis project! In this analysis, we dive deep into an epic battle between Liverpool and Tottenham Hotspur, exploring key statistics, tactical insights and player performances, that shaped the outcome of one of football's most prestigious matches.

Key Findings:
- Team Statistics: We examined various team statistics, including shots, expected goals (xG), passes and other key performance indicators, providing a comprehensive overview of each team's performance on the pitch.

- Tactical Analysis: Our analysis includes detailed player statistics such as shot distribution, passing networks, and pressure heatmaps, offering insights into individual player contributions and playing styles.

- Visualizations: We utilized the mplsoccer library to create visualizations such as shot maps and passing networks and heatmaps, providing intuitive representations of match dynamics and player interactions.

- Dashboard: Additionally, we developed an  dashboard using Tableau, offering detailed statistics and insights into the performance of each player during the UEFA Champions League Final.

## Installation

1. Python: Set up a Python environment suitable for running the analysis scripts or Jupyter notebooks. You may use Anaconda or create a virtual environment.

2. Dependencies: Make sure you have the required Python libraries installed. In this project we will use data and a lot of functions from the mplsoccer library. You can install it using pip:
     ```python
     pip install mplsoccer 
     ```
     - pandas
     - matplotlib
     - scipy

3. Power BI 
- Power BI Desktop: Download and install Power BI Desktop from the official [website](https://powerbi.microsoft.com/en-us/desktop/)
- Open Dashboards: After downloading the [dashboard](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/UCL%20Final%202019.pbix) file, you can open it using Power BI Desktop.

4. Tableau Dashboard:
 - Utilized Tableau for insightful data visualization and analysis.
 - To access the Tableau dashboard, click [here](https://public.tableau.com/app/profile/leonidas.emmmanouilidis/viz/UCLFinal2019_17133834605920/Dashboard1)
## Data   

1.  The data for this analysis was obtained using the __mplsoccer__ library, which provides functionalities for accessing football match data. Here's a breakdown of the retrieval process:
```python
from mplsoccer import VerticalPitch, Pitch, create_transparent_cmap, FontManager, arrowhead_marker, Sbopen
```
2.  Data Retrieval: We utilized the parser module from the mplsoccer library to retrieve specific data related to the UEFA Champions League Final 2019.
```python
df_competition = parser.competition()
df_match = parser.match(competition_id=16, season_id=4)
df_lineup = parser.lineup(22912)
df_event, df_related, df_freeze, df_tactics = parser.event(22912)
```
3.  Dataframe Selection: Among the retrieved dataframes, we primarily utilized df_event for our analysis, as it contained the relevant match event data.


## Game-Analysis  
  ### Match Score
  In the UEFA Champions League final of 2019, Liverpool achieved a victory against Tottenham Hotspur with a score of __2-0__. The match showcased Liverpool's passion and clinical finishing, securing their sixth European title. 

  ### Lineups
  
  The following visualization presents the lineups for both teams accompanied by individual heatmaps showcasing the on-field activity of each starting player. A heatmap serves as a graphical representation of a player's actions throughout the game, involvement in ball-related activities, and positional coverage on the field. This visualization offers valuable insights into each player's performance and tactical contributions during the match.

  
   ![lineups_plot](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/lineups_heatmaps.png)



  ### Expected Goals
  
  Expected Goals (xG) in football evaluates the quality of scoring opportunities, offering deeper insights beyond traditional statistics like goals scored, by assessing the likelihood of scoring based on various factors.  
  
   ![xG](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/sum_xG.png)

  By visualizing the xG values on a minute-by-minute basis, we can analyze the scoring opportunities created by both teams and track the __momentum__ shifts during the match. Here's a line 
  chart by use of Power BI showcasing the progression of scoring opportunities, measured by minute, for both teams during the game.  
 
   ![xG_sum](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/sum_xg_final.PNG)  

   It's important to note that Liverpool scored at the beginning of the game (1') with a penalty. That's why the xG at the start of the game is at 0.78 xG.

  ### Passing Networks  
  A passing network in football refers to a visual representation or analysis of the passing interactions between players on a team during a match. Passing networks can provide insights into the patterns of play, teamwork dynamics, and strategies employed by a team during a match. They can reveal which players are involved in the build-up of play, how possession is circulated, and the effectiveness of passing connections between different areas of the pitch.   

![Liverpool_Pass_Netw](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/Liverpool_Passing_Network.png)    

In a passing network, the thickness of a line between two players represents the frequency or volume of passes exchanged between them. When the line between two players, such as left-back (LB) with left-winger (LW) as above, is thick, it signifies a high number of passes between them. This indicates that those players are heavily involved in passing exchanges, often playing a significant role in the team's build-up play or in circulating possession from deep positions.  

![Tottenham_Pass_Netw](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/Tottenham%20PassNetw.png)  

  ### Pressure Heatmaps  
  A pressure heatmap in football, also known as a pressing heatmap or pressure map, visualizes the intensity and location of defensive pressure exerted by a team on their opponents during a match. It provides insights into how effectively a team applies pressure on their opponents to disrupt their play, regain possession, or force them into making mistakes.  

  - Liverpool's heatmap highlights the high pressing strategy of the team. Liverpool aimed to win back possession of the ball quickly by putting intense pressure on the opponent's players as soon as they enter the attacking half.
   
 ![Liverpool_Heatmap](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/final_liverpool.png)

 - On the other hand, since Tottenham had the possession of the ball most of the time, the heatmaps don't show the defensive intensity and pressure that Liverpool had during the game. However, it's obvious that Tottenham chose to press Liverpool's left back (Robertson) and right winger (Salah) who had a solid game, as we will se later.
  
 ![Tottenham_Heatmap](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/final_tottenham.png)

  ### Total Shots:
  The following visualization shows the total shots of each team including the shots that was on target.

   ![total_shots](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/total_shots.png)

  ### Total Passes/Accuracy(%)
  Tottenham was more dominant in ball traffic, making more passes overall and significantly greater passing accuracy (79.3%) compared to Liverpool (62.0%), showcasing their control and precision in possession during the match.

   ![total_passes](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/total_passes.png)  

 #### Passing Arrows Map  
 Passing arrows maps are powerful visual tools that help teams and analysts evaluate passing dynamics, identify strengths and weaknesses, and make informed decisions to optimize their 
 tactical strategies.    

 - The passing arrows map below highlights Liverpool's desire to attack and build up from the left side, utilizing Robertson and Mane. Successful passes are more frequent from this area, indicating a focused effort to exploit the left flank.

 ![Liverpool_pass_arrow](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/liverpool_arrow.png)   

  
 - On the other hand, it's obvious that Tottenham had way more passes escpecially in their own half. However, the successful passes in the final third of the court is significantly decreased, which is showcasing the solid Liverpool's defense.

 ![Tottenham_pass_arrow](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/Tottenham_Arrows.png)  


  ### Total Dribbles
  The following plot focuses on the dribbles each team attempted during the game, including the successful attempts.  

   ![total_dribbles](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/total_dribbles2.png)

  Liverpool completed 2 successful dribbles out of 6 attempts, while Tottenham achieved 4 successful dribbles out of 9 attempts, achieving a higher success rate during the match.

  ### Aerials Won  
  
  The next plot focuses on the aerials attempts during the game.  
  
  ![aerial_won](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/aerial_wons.png)  

  Liverpool outmatched Tottenham in successful aerial attempts, winning 18 of them.  

  ### Shots Map   
  
  In the following shot maps we can see the locations of shots taken by Liverpool's and Tottenham's players during the match. The bigger the marker is the greater the expected goal of the corresponding shot. It's obvious that the biggest chance for Liverpool based on the xG was the penalty that had at the beginning of the game (1'), when Salah scored.  

  ![shot_maps](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/shots_maps_final_see.png)  


  ### Players's Contribution  

  Next, we've developed a Tableau dashboard showcasing the distribution of diverse football metrics attributed to players. These include statistics like shots taken, aerial duels won, and possession indicators such as passes, ball receipts, and carries. In addition, the table in the top right corner displays players' shots, detailing each shot's outcome and its corresponding expected goals (xG) value.  

  ![dashboard](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/Dashboard%201.png)    
  
  - We observe that Salah had the most scoring attempts (6 shots) during the game and the most ball receipts (52) too. Sadio Mane is second in the ball receipts with 45 for Liverpool.Robertson is the player with the most passes (54) and carries (29) for Liverpool with Trent Alexanter Arnold in the second place with 47, highlighting Liverpool's strategic emphasis on using their wide players to create scoring opportunities.
  - Matip and Vertonghen won the most aerial duels during the game.
  - Finally, we confirm the Tottenham's possession dominance, since the defenders dominated in passing, ball receipts and carries. 
    

  
                     
  
