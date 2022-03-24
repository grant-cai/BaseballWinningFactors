# Winning Factors in Baseball Data Exploration

## Description

### Background

Baseball is not only one of the oldest professional sports played in the United States, 
but also one of the sports that has become increasingly interested in statistics over the 
years. As the technological means have developed over the decades, the sport has adopted them 
to gather more and more data about the game. What started off with simple tallying and
tracking by individuals is now a sport with high-framerate cameras and radar guns. This
collection of data has all served the core purpose of allowing teams to extrapolate useful
information in order to win ball games. 

### Goal

The purpose of this project was to conduct a data exploration into some of the very basic
metrics that occur during a baseball game using various types of statistical modeling
in order to determine which factors most heavily influenced a team's ability to win a game 
or not.

While it makes intuitive sense that the team that gets the most hits and avoids letting
opponents on base will have a greater chance of winning the game, we hoped that our data
analysis would yield more insightful results into other events that take place during the
game that might influence a team's ability to win.


## Data Gathering

Data was gathered from the 1980 Major League Baseball season to the 2021 season from the 
website [Retrosheet](https://www.retrosheet.org/) under the website's `gamelogs` section. 
The CSVs from the above seasons were then compiled into one large dataset with nearly 
100,000 observations. The specific variables in the dataset were rather extensive, 
including the expected columns of runs scored for each  team, the number of hits, the 
number of at bats, etc., but also included several interesting variables for further 
analysis, including the number of times each team grounded into a double or triple play, 
the number of runners left on base, the number of pitchers used, and the number of times
each team was caught stealing. The dataset also included many qualitative variables, including
whether the game was played at night, the umpires at each position, as well as the entire 
starting lineup for each team. The full gamelog file used can be found in the repository.

### Data Cleaning

The purpose of the project was to utilize some of the above variables as predictors in a
model to determine which team would win. The gamelogs did not come with a `Winner` column
by default, so one was coded in Python and appended to the dataset.

Naturally, this became a classification problem, and with over 160 columns of data to 
parse through, it was necessary to determine which columns were more important towards our end goal.
Running classification models on this data necessitated the removal of many qualitative
predictors in the data. The predictors utilized were `Date`, `NumberOfGame`, `VisitTeam`, 
`VisitLeague`, `VisitTeamGameNumber`, `HomeTeam`, `HomeLeague`, `HomeTeamGameNumber`, 
`VisitTeamScore`, `HomeTeamScore`, `GameLength`, `DayNight`, `Attendance`, 
`VisitTeamAB`, `VisitTeamH`, `VisitTeamDoubles`, `VisitTeamTriples`, `VisitTeamHR`, 
`VisitTeamRBI`, `VisitTeamSacHit`, `VisitTeamHBP`, `VisitTeamBB`, `VisitTeamIntentBB`, 
`VisitTeamK`, `VisitTeamSB`, `VisitTeamCaughtStealing`, `VisitTeamGroundIntoDoublePlay`, 
`VisitTeamCatcherInterference`, `VisitTeamLOB`, `VisitTeamPitchersUsed`, `VisitTeamIndividualER`, 
`VisitTeamER`, `VisitTeamWildPitches`, `VisitTeamBalks`, `VisitTeamPutouts`,
`VisitTeamAssists`, `VisitTeamErrors`, `VisitTeamPassedBalls`, `VisitTeamDoublePlay`, 
`VisitTeamTriplePlay`, `HomeTeamAB`, `HomeTeamH`, `HomeTeamDoubles`, `HomeTeamTriples`, 
`HomeTeamHR`, `HomeTeamRBI`, `HomeTeamSacHit`, `HomeTeamHBP`, `HomeTeamBB`, `HomeTeamIntentBB`, 
`HomeTeamK`, `HomeTeamSB`, `HomeTeamCaughtStealing`, `HomeTeamGroundIntoDoublePlay`, 
`HomeTeamCatcherInterference`, `HomeTeamLOB`, `HomeTeamPitchersUsed`, `HomeTeamIndividualER`, 
`HomeTeamER`, `HomeTeamWildPitches`, `HomeTeamBalks`, `HomeTeamPutouts`, `HomeTeamAssists`, 
`HomeTeamErrors`, `HomeTeamPassedBalls`, `HomeTeamDoublePlay`, `HomeTeamTriplePlay`, `Winner`, and `Year`.