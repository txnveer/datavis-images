# CS 424 Project 2
## Premier League Data Visualization Using d3.js in Observable
This project was done in d3.js using the Observable notebook.
Link to the Observable notebook: https://observablehq.com/@txnveer/premierleague2122datavisualization
#### Dataset Description and Data Pre-Processing
The dataset was collected from Opta consists data of the 20 teams with respect to team stats in the league, and 546 players that played during the Premier League season of the year 2021/2022.
The data was split into two dataframes, the team dataframe and players dataframe. The team dataframe consisted of 15 attributes and the players dataframe consisted of about 22 attributes. Furthermore, I had dropped some more attributes in the players dataframe and the a row of data looked like this:

*name: "Son Heung-min", nation: "kr KOR", position: "MFFW", squad: "Tottenham", age: "29", played: "35", goals: "23", assists: "7", nonPKgoals: "23", PKgoals: "0", expected: "15.6", nonPKexpected: "15.6", yellows: "2", reds: "0"*

Likewise a row of the team data looked like this after dropping of some attributes:
*league_position: "1", squad: "Manchester City", points: "93", wins: "29", draws: "6", loss: "3", goals: "99", conceded: "26", goaldifference: "+73", expectedgoals: "96.6", expectedconceded: "26.0", expectedGD: "+70.5", ticketsales: "52774"*

There were no null values, nor missing values in this dataset, I dropped the players that had played less than 5 games for the season which is about 10% of the total matches in the season, this was done to reduce players with let's say only one or two games played at the end of the season. This reduced the number of players from 546 to 444 players. 


#### Domain and Questions
The domain for asking questions for this dataset was on player performance and team performance. The questions were as follows:
- **Q1.** Which teams performed the best during the season? And see if teams that perform better have better ticket sales?
- **Q2.** What was the player performance distribution based on goals and assists for each team? And to see if there were any standouts for the teams.
- **Q3.** Which type of players were the top performers and trends?

#### Bar Chart Visualization Used to Analyze the Team Stats

###### Bar Chart based on amount of points
[![leaguetable](https://github.com/txnveer/datavis-images/blob/main/barchart_points.png "leaguetable")](http://https://github.com/txnveer/datavis-images/blob/main/barchart_points.png "leaguetable")
###### Bar Chart based on amount of goals scored
[![GoalsScored](https://github.com/txnveer/datavis-images/blob/main/barchart_goals.png "GoalsScored")](https://github.com/txnveer/datavis-images/blob/main/barchart_goals.png "GoalsScored")
###### Bar Chart based on average attendance/ticket sales
[![AverageAttendance](https://github.com/txnveer/datavis-images/blob/main/barchart_attendance.png "AverageAttendance")](https://github.com/txnveer/datavis-images/blob/main/barchart_attendance.png "AverageAttendance")

To get the input for which attribute we wish to do visualization, we use a dropdown box that contains the attributes, which when selected, we get a bar chart based on that visualization. Here I also kept them in the same order where they finished in the table, so we can quickly compare between different attributes selected. The other interactive element is whenever we hover, we are able to see other information of the team as well, which was done using tooltip and mouseover and mouseout to get this visualization. (But for this, I used d3 version 5 to work, which was needed to not be initialized for the rollup function to work to collect the count and also for InternSet to work in the pie chart visualization)

The information provided by this visualization was that the teams that had a better performances were generally the one that finished higher on the league, but there were some anomalies such as Manchester United were the only team to have a non-positive goal difference and Crystal Palace were the only team in the bottom 12 to have scored more goals than conceded.

Average ticket-sales/attendance was interesting to see, as Manchester United still had the highest amount despite not playing ‘well’. Manchester City and Liverpool were 5th and 6th despite performing extremely well, this is more likely to do with the stadium capacity of the teams. But it’s still interesting to see that fans will buy tickets even if their team is not playing up to their standard. This answers our questions in **Q1.**

#### Scatter plot used to visualize goal contributions by each player in the form of goals and assists for each team
The interactive elements in this visualization is the drop down to select the team and hover over which gives us the details of the player.
[![Scatter_liverpool](https://github.com/txnveer/datavis-images/blob/main/scatter_liverpool.png "Scatter_liverpool")](https://github.com/txnveer/datavis-images/blob/main/scatter_liverpool.png "Scatter_liverpool")

This visualization was able to show outliers, the players that had performed very well for their respective team. For example Salah’s contributions were so good compared to any of their teammates.

[![Norwich_scatter](https://github.com/txnveer/datavis-images/blob/main/scatter_norwich.PNG "Norwich_scatter")](https://github.com/txnveer/datavis-images/blob/main/scatter_norwich.PNG "Norwich_scatter")

Looking at the other teams, there was a distinct pattern of as lower down the table we go, teams had lesser contributions and the contributions from the players were generally more bunched up together, except for a couple anomalies such as Ivan Toney from Brentford, Teemu Pukki from Norwich, Emmanuel Dennis from Watford. This answers the questions we had in **Q2.**

#### Pie chart used for visualizing for top 20 players by position they play

###### Pie chart based on assists for the top 20 players
[![pie_assist](https://github.com/txnveer/datavis-images/blob/main/piechart_assist.png "pie_assist")](https://github.com/txnveer/datavis-images/blob/main/piechart_assist.png "pie_assist")
###### Pie chart based on yellow cards for the top 20 players
[![pie_cards](https://github.com/txnveer/datavis-images/blob/main/piechart2.PNG "pie_cards")](https://github.com/txnveer/datavis-images/blob/main/piechart2.PNG "pie_cards")
For the interactive part, I have used a radio selection in which when clicked on we get the visualization based on that attribute, and like the previous visualization this gave us the details of the 'pie', like the position, count, and the percentage of it in the top 20.

Here we see that for goals scored (either non-PK, PK or total), it is mostly forwards and midfielders. For assists we are able to see defenders in the mix. For yellow cards we see that there is a much more equal distribution with among defenders, midfielders and attackers.

It is also interesting to see, that especially for attributes regarding goal contributions (Goals & Assists), we were able to see that the top players usually had one preferred position, and only difference in preference was for forwards (like FW, FWMF, MFFW), but for the rest, defenders and midfielders, their preferred positions were either DF or MF respectively. So, we can conclude, that the top players are more likely to play in position, especially for defenders and midfielders. Forwards seem to be more flexible but that might be due to the positions the manager tries to fit them in a formation. Thus, we are able to answer the questions in **Q3.**

#### Multiple Linked view visualization used with brushable scatter plot linked to bar chart

###### Scatter plot linked with bar chart for 'X' variable vs 'Y' variable which can be chosen
[![Brush](https://github.com/txnveer/datavis-images/blob/main/brushable_1.PNG "Brush")](https://github.com/txnveer/datavis-images/blob/main/brushable_1.PNG "Brush")
###### Brushable scatter plot linked to bar chart as seen below
[![Brush2](https://github.com/txnveer/datavis-images/blob/main/brushable_2.PNG "Brush2")](https://github.com/txnveer/datavis-images/blob/main/brushable_2.PNG "Brush2")

I have gone with a brushable scatter plot linked to a bar chart to get a clearer view on the number of players on the scatterplot especially in those areas where there is overlapping in the denser areas of the scatter plot, since our dataset has mostly integer values there will be overlapping of values, hence it felt important to link a bar chart to see the distribution as well. The brushable visualizations were done with the help of .on() command.










