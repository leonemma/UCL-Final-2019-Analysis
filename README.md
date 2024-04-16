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
- __Match Score__:
  ```python
  liverpool_goals = df_event[(df_event['outcome_name']=='Goal') & (df_event['team_name']=='Liverpool')].shape[0]
  tottenham_goals = df_event[(df_event['outcome_name']=='Goal') & (df_event['team_name']=='Tottenham Hotspur')].shape[0]
  print(f'Liverpool {liverpool_goals}:{tottenham_goals} Tottenham Hotspurs')
  ```
  Liverpool 2:0 Tottenham Hotspurs

- __Expected Goals__:
  
Expected Goals (xG) in football quantify the quality of scoring opportunities, offering deeper insights beyond traditional statistics like goals scored. By assessing the likelihood of scoring based on various factors, xG provides a more comprehensive evaluation of team performance and strategy.  

  ```python
  team1_xG = by_team['shot_statsbomb_xg'].sum().values[0]
  team2_xG = by_team['shot_statsbomb_xg'].sum().values[1]
  print(f'Liverpool xG: {team1_xG:.2f}')
  print(f'Tottehnam xG: {team2_xG:.2f}')
  ```
   - Liverpool xG: 1.20
   - Tottehnam xG: 0.92

 By visualizing the xG values on a minute-by-minute basis, we can analyze the scoring opportunities created by both teams and track the momentum shifts during the match. Here's a line chart by use of Power BI showcasing the progression of scoring opportunities, measured by minute, for both teams during the game.  
 
![Plot1](/plots/edw.PNG)


- __Aerial Won__:
  ```python
  team1_aerialW = by_team['aerial_won'].sum().values[0]
  team2_aerialW = by_team['aerial_won'].sum().values[1]
  print(f'Liverpool Aerial Wons: {team1_aerialW}')
  print(f'Tottehnam Aerial Wons: {team2_aerialW}')
  ```
   - Liverpool Aerial Wons: 18
   - Tottehnam Aerial Wons: 14

- __Total Shots__:
  ```python
  team1_shot_cnt = df_event[(df_event['type_name']=='Shot') & (df_event['team_id']==24)].shape[0]
  team2_shot_cnt = df_event[(df_event['type_name']=='Shot') & (df_event['team_id']==38)].shape[0]
  print(f'Liverpool Total Shots: {team1_shot_cnt}')
  print(f'Tottehnam Total Shots: {team2_shot_cnt}')
  ```
   - Liverpool Total Shots: 14
   - Tottehnam Total Shots: 16
  


  
