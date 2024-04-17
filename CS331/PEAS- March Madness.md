# 1
Performance Measure:
* Accuracy: How many answers are we getting right, and how many answers are we getting wrong
	* Minimize incorrect predictions
	* Maximize correct predictions
	* Must consider the probabilities predicted by the model
		* If the model predicts a team will win with a 99.9% confidence score, and they lose then the model should receive a lower performance score than if it had predicted a win with a lower confidence score.

Environment:
* Team Statistics: points per game, rebounds per game, assists per game, blocks per game, steals per game, field goal percentage, three pointers made, three point percentage, free throw percentage, three point percentage.... etc.
* Individual Statistics: points per game, rebounds per game, assists per game, blocks per game, steals per game, field goal percentage, three pointers made, three point percentage, free throw percentage, three point percentage.... etc.
* Injury Report
* Team vs Team Record
* Coach vs coach record
* Player vs Player record
* Length of time between games
* Location of Match
* Team distance from match location
* Travel Time
* Home win/loss record
* Away win/loss record
* Neutral win/loss record
* Starting Roster
* Referee Assignment

Actuators: 
* The location that the prediction will be displayed. Could be represented as a:
	* Printed bracket
	* Website displaying predictions
	* Command line terminal
* Anywhere that we would want the model to take an action on its prediction

Sensors:
* Data Pipeline: Ideally this could be done with API calls, but if that is not the case, data scrapers could be used to populate a database and queried for the information.

# 2

**A model-based reflex agent would be an excellent choice here because of the task of predicting March Madness outcomes. A simple reflex agent could easily be deployed by selecting the team with the higher win percentage each time, but this is too simple to get accurate predictions from. A simple agent is not complex enough for this problem, and a lookup table to see who would win is almost impossible to build without other information. Sure, you could calculate the probabilities, but that is a lot of extra work. Then, when it comes to goal-based and utility-based agents, both of these agent types could be deployed here, but because our agent's actions do not produce consequences within the environment their use cases do not fit the needs of our problem. There is no need to measure how the actions of our agent will affect the future because the actions of our agent do not affect the outcome of the tournament. Instead, we can evaluate the state given at each round of the bracket, and use the precept history to help inform the prediction of our model-based reflex agent.**