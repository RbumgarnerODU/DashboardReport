
# Dashboard Final Report
### Robert Bumgarner
### Information Visualization
### CS 725, ODU, Spring 2025
## MLB Farm Team Assessment using WAR and Debut Timelines
![Image of information visualization dashboard](Dashboard.jpg)
 - ## Introduction
Baseball is an excellent topic for an information visualization project due to its rich and structured data. The sport has a long-standing tradition of meticulous record-keeping, with statistics recorded for nearly every aspect of the game—from player performance metrics like batting average, on-base percentage, and strikeout rates, to team-based analytics such as win-loss records and run differentials. This wealth of data provides a fertile ground for creating detailed visual representations that can reveal patterns, trends, and insights over time. These trends can provide a valuable tool for teams to make strategic decisions with their player development, player acquisitions, or game strategies.

Moreover, baseball appeals to a broad audience, including fans, analysts, and fantasy sports enthusiasts, all of whom benefit from clear, engaging visualizations. Well-designed graphics can help explain complex statistical aggregations like Wins Above Replacement (WAR) or compare many players' performances in a more intuitive way. Interactive dashboards, heatmaps, spray charts, or pitch tracking plots can enhance the viewer’s understanding and appreciation of the sport’s nuances.

I can recall countless times when a baseball commentator during a baseball broadcast comments that 'the player hasn't had enough time in the minor leagues' when the new players appear to struggle in their new role. The MLB draft talent pipeline begins with amateur players—primarily high school and college athletes—who are scouted over several years through showcases, tournaments, and school seasons. Each summer, eligible players enter the MLB Draft, where teams select from this pool in reverse order of their teams' previous season’s standings. After being drafted, players typically sign contracts and begin their professional careers in the Minor League system, progressing through levels (Rookie, A, AA, AAA) based on performance and development needs. It is this development process (or lack thereof) which commentators tend to suggest is a cause for the players' apparent successes or failures.

It was my hope for this project to provide a data dashboard capable of demonstrating any MLB teams' ability to draft and develop player talent by showing a trend in increased overall player performance as the time from drafting to debut increases. Along with this displayed data, I hoped to include relevant fielding, pitching, and batting stats while also allowing a user to filter by important player characteristics such as handedness and positions played.

![An image of suspected possible trends across league](Trends.jpg)
 - ## Data
The data for this project originates from 4 datasets from the www.baseball-reference.com page. 
 - [Rookie Stats](https://www.baseball-reference.com/leagues/majors/2021-rookies.shtml)
 Contains great info about WAR during the rookie year, draft times, and handedness for batting and throwing. The draft and debut dates are used in deriving a time-to-debut statistic which plots the x-axis of the main scatterplot. Positions in this dataset are quite convoluted with positions divided into those where the player played >60% of the season's games, at least 10 games, and less than 10 games. This field was difficult to parse and ended up as a truth table of consistently played positions as well as a single string representation of the players most played positions as digits 1-9 and D for designated hitting. Data spans 11 years of baseball stats (11 chosen for no particular reason) from 2014-2024. 
 - [Fielding Stats](https://www.baseball-reference.com/leagues/majors/2024-fielding-leaders.shtml)
 - [Pitching Stats](https://www.baseball-reference.com/leagues/majors/2024-pitching-leaders.shtml)
 - [Batting Stats](https://www.baseball-reference.com/leagues/majors/2024-batting-leaders.shtml)
These 3 last stat fields were joined to the modified rookie debut dataset as merged data frames. The site had a csv export option for each years table but not a comprehensive year-to-year dataset, so data downloading and joining all years was performed manually. Afterwards, data was merged via pandas dataframes merge() methods using a unified statistic which is the database's shortest possible player name to give them a unique identifier. Picture a string which names two John Smiths appropriately so they have unique identifiers with the least possible characters.

The scripts and raw data processed prior to upload to observable are all present here along with a SHAP analysis utilizing ML to derive the most influential predicters of a player's WAR:
[Link to Data Manipulation Zip](PythonWork.zip)

 - ## Visualization

 The dashboard possesses 5 total visualization elements outside of the interactive inputs included to filter data and change interactive behaviors:
 
 - **WAR vs. Debut Time Scatter Plot**
 This plot presents the user with a view of all players in the current dataset with their WAR stat as the vertical axis (a comprehensive aggregated stat of the players performance) and their time to debut. The debut time is measured in years as the time from their drafting or free agent signing to their first debut game in their rookie season. A sweeping filter is provided to allow the user to change the data displayed in the subsequent charts and a tooltip feature provides player name and displayed statistics for the mark hovered over. Users shift clicking the mark can also initiate a google search with the players, name, team, and rookie year.
 ![scatter](Scatter.jpg)
 - **Player Counts by year -*or*- Player Counts by Team Bar Chart**
 This plot, depending on the number of teams present on the chart, denotes the number of players in the current filtered dataset. When the user sweeps through a section of the scatter plot, this plot changes to reflect counts in the selected region.
 ![Bar](Bar.jpg)
 - **Box and Whisker Plots with Key baseball Statistics and a Scatter Overlay**
 These plots denote a league-derived value by year for the box-and-whisker plot statistics displayed in each facet. Overlayed over each plot is a scatter mark for the filtered player values present in the current data set. Extra filtering is performed to ensure players who have not pitched do not show up in the ERA and pitchers who only pitch and do not bat are not displayed with a batting average. A tooltip allows further determination of the player mark shown. 
  ![BWwO](BoxWhiskerWithOverlay.png)
 
 - ## Design Decisions
	 - Visual Encodings
	 - Principles
	 - Interactive Justifications
 - ## Development Process
 - ## References
	 - [enter link description here](ReferenceLink)
	 - [enter link description here](ReferenceLink)
	 - [enter link description here](ReferenceLink)
	 - [enter link description here](ReferenceLink)
