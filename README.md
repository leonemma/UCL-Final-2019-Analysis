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
- Team Statistics: We examined various team statistics, including total shots, sum of expected goals (xG), and aerial duels won, providing a comprehensive overview of each team's performance on the pitch.

- Tactical Analysis: Our analysis includes detailed player statistics such as shot distribution, passing networks, and pressure heatmaps, offering insights into individual player contributions and playing styles.

- Visualizations: We utilized the mplsoccer library to create visualizations such as shot maps and passing networks, providing intuitive representations of match dynamics and player interactions.

- Dashboard: Additionally, we developed an interactive dashboard using Power BI, offering detailed statistics and insights into the performance of each player during the UEFA Champions League Final.

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
  ### Match Score:  
  In the UEFA Champions League final of 2019, Liverpool achieved a victory against Tottenham Hotspur with a score of __2-0__. The match showcased Liverpool's passion and clinical finishing, securing their sixth European title. 

  ### Lineups
  
  The following visualization presents the lineups for both teams accompanied by individual heatmaps showcasing the on-field activity of each starting player. A heatmap serves as a graphical representation of a player's actions throughout the game, involvement in ball-related activities, and positional coverage on the field. This visualization offers valuable insights into each player's performance and tactical contributions during the match.

  
   ![lineups_plot](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/lineups_heatmaps.png)



  ### Expected Goals:
  
  Expected Goals (xG) in football evaluates the quality of scoring opportunities, offering deeper insights beyond traditional statistics like goals scored, by assessing the likelihood of scoring based on various factors.  
  
   ![xG](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/xG.png)

  By visualizing the xG values on a minute-by-minute basis, we can analyze the scoring opportunities created by both teams and track the __momentum__ shifts during the match. Here's a line 
  chart by use of Power BI showcasing the progression of scoring opportunities, measured by minute, for both teams during the game.  
 
   ![xG_sum](/plots/xG_sum_snap.PNG)


  ### Total Shots:
  The following visualization shows the total shots of each team including the shots that was on target.

   ![total_shots](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/total_shots.png)

  ### Total Passes/Accuracy(%)
  Tottenham was more dominant in ball traffic, making more passes overall and significantly greater passing accuracy (79.3%) compared to Liverpool (62.0%), showcasing their control and precision in possession during the match.

   ![total_passes](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/total_passes.png)

  ### Total Dribbles
  The following plot focuses on the dribbles each team attempted during the game, including the successful attempts.  

   ![total_dribbles](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/total_dribbles.png)

  Liverpool completed 2 successful dribbles out of 6 attempts, while Tottenham achieved 4 successful dribbles out of 9 attempts, achieving a higher success rate during the match.

  ### Aerials Won  
  
  The next plot focuses on the aerials attempts during the game.  
  
  ![aerial_won](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/aerial_corrected.png)  

  Liverpool outmatched Tottenham in successful aerial attempts, winning 18 of them.  

  ### Shots Map   
  
  In the following shot maps we can see the locations of shots taken by Liverpool's and Tottenham's players during the match. The bigger the marker is the greater the expected goal of the corresponding shot. It's obvious that the biggest chance for Liverpool based on the xG was the penalty that had at the beginning of the game (1'), when Salah scored.  

  ![shot_maps](https://github.com/leonemma/UCL-Final-2019-Analysis/blob/main/plots/shots_maps_final_see.png)  

  ### Passing Network

  
  <iframe src="https://public.tableau.com/app/profile/leonidas.emmmanouilidis/viz/UCLFinal2019_17133834605920/Dashboard1?publish=yes" width="800" height="600"></iframe>

  
                     
  
