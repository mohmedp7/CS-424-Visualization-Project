# CS 424 Assignment 3

#### Aidan Pina
#### Mohmed Patel



# Task 1: Implementing interaction

The visualization that we decided to use was the trend chart of ending bids by item order for each livestream. This visualization addresses my question of how prices evolve over the course of a stream and how different formats affect it. The static version displays all eight livestream trend lines on a single chart with a color-coded legend showing individual streams and line styles showing stream formats (solid vs. dotted). Because all data is visible at once without manipulation, it serves as a complete, fair baseline where participants can answer any analytical question through visual scanning and legend lookup. The interactive version of this visualization gives it a dropdown filter where the user can select between all sudden death streams, all auction streams, and each stream individually. We believe that this interaction will help answer analytical tasks because it allows users to filter out irrelevant streams (example could be hiding Sudden Death lines when analyzing Auction streams), the interaction reduces visual noise and the amount of lines on the graph, which we expect will improve speed and precision during comparisons and trend-based tasks.


# Task 2: Evaluation design

We plan to evaluate whether introducing interactive filtering into the data visualizations will improve participants' ability to identify differences in endings and trends between streams compared to a static visualization. We believe that the participants will complete the analytical tasks faster when using the interactive visualization than the static because filtering will allow the removal of clutter or unnecessary visual information depending on what the task calls for.

  

The procedure I plan to use is to spend an untimed portion of the interview/evaluation giving some context and explaining the general data. The people I will be interviewing will have never seen Whanot or used it in order to make sure that none of the answers given could be from prior knowledge or experience. But I did think preparing them with some information about what they’ll be seeing and what it means was beneficial to getting the most accurate measurements when the evaluation begins.

  

I began each evaluation with the same minor context to get the participants to have a minimal understanding of where the data came from and what it means. This included what SD was, the difference between SD and auction streams, and what ending bids were. Then once that was finished I began the timer and asked the series of questions while recording both the time it took for each task individually and the full interview time including asking the questions. We changed the starting visualization at the 6th participant in order to counterbalance. Participants were allowed to ask any questions during the interview and that was included in the times recorded.

| Analystical Task  | Static	 | Interactive | 
| -------------|:-------------:|:-------------: 
|Identify a Max/Min |Looking at only the auction streams , which stream reached the highest ending bid, and approximately how much higher was it than the lowest|Looking at only the Sudden Death streams, which stream reached the lowest ending bid, and approximately how much lower was it than the highest|
|Compare Trends|Which of the auction streams shows the largest increase in ending bids from the beginning to the end? |Which of the SD streams shows the lowest change in ending bid from the beginning to the end?


The questions above are the 4 tasks that were split and measured when given to each participant, meant to be not very difficult but also not something that can be answered instantly. They are also able to assess the same analytical skills without leaving room for memorization or lucky guessing. The goal was to give questions that would take time but not too much time so that the data collected can truly be accurate and relied on to tell if there is a better efficiency in one visualization versus another. As for expected answers we were looking for close estimates rather than exact value matches but for the static max/min question an acceptable and expected answer would be newfriendvtg | Hec’s Personal Shop and a value of around 10. For the static trend comparison an acceptable and expected answer would be either of the 2 newfriendvtg stream trends. As for the interactive max/min we were looking for Mrtop | Premium Sports Show with a difference of around 170, then for the trend comparison we would accept and expect Mrtop | Premium Sports Show.

Once answers were given and times were recorded I put the time each task took and the time of the whole interview into an excel sheet and recorded accuracy as well, as long as the answers were within reason then they were accepted as correct.

## Task 3: Conducting the Evaluation
Data: https://github.com/mohmedp7/CS-424-Visualization-Project/blob/main/EvaluationData(Sheet1).csv

The evaluation was conducted with 10 participants, excluding those used in the initial pilot tests. Each participant completed the four analytical tasks using both the static and interactive visualizations following our procedure stated in Task 2.

  

Before conducting the full evaluation, the pilot test helped identify potential issues with the questions we originally came up with, visualization ideas, and the measurements we'd record. Based on the pilot, we settled on a dropdown filter for the interactive chart visualization showing ending bids while the streams were live. We also refined our questions from simplistic “what is the highest ending bid?” to more fleshed out questions that would take more thinking like “Which stream reached the highest bid?” and asking the participant to compare the highest and lowest points to get a value estimate.

  

Throughout the evaluations, we recorded each participant's accuracy, individual task completion times, and total interview duration. Participants were assigned anonymous identifiers to maintain privacy in our Excel sheet.

## Task 4: Quantitative analysis 

Based on our data, all 10 participants completed all 4 questions with the correct responses. This means that our task accuracy for both static and interactive visualizations is 100%. 

<img width="480" height="182" alt="image" src="https://github.com/user-attachments/assets/85f4b7bf-3882-4099-90b7-6346ff2a73ee" />


<img width="896" height="494" alt="image" src="https://github.com/user-attachments/assets/d5f32fd4-c450-4747-a9ad-1adcea740f8f" />


<img width="597" height="393" alt="image" src="https://github.com/user-attachments/assets/130b1758-7296-443b-abfc-34fca00bd4aa" />





Looking more deeply into the summary statistics for each question, we can see some patterns between the two tasks. For the participants' first task, the average time was 59.7 seconds for the static version and 51.7 seconds for the interactive version. The interactive version was slightly faster, which supports our hypothesis. Looking at the task 2 values, participants averaged 50.7 seconds for the static version and 36 seconds for the interactive version. This agains helps us support our hypothesis because the interaction saved us an average of 14.7 seconds. However, given that it's only 10 responses and that these values aren't that far apart,  we can't be for certain that interactions are better. 

One big thing we noticed was that whichever task a participant did first, it took considerably longer. Then, as they became accustomed to the graph, their response time dropped significantly. We think this was because they became familiar with the visualization and could read it more efficiently. 

In the end, while interactive filtering provided a slight speed advantage on the trend comparison task, it did not substantially alter overall performance because, as we will explain in Task 5, many participants bypassed the category filters and chose to view all streams at once, effectively replicating the static chart.
 



## Task 5: Reflection and Recommendations 

We hypothesized that the interactive chart would be more efficient or useful than a static chart with more visual clutter. However, after reviewing the results and times, there wasn't a noticeable difference in participants' performance, either in accuracy or time. 
But something that isn't reflected in the data is the participants' personal preferences, which was very surprising, seeing as many participants would opt for the dropdown filter option that showed all 8 streams at once regardless of the question asked. 
A belief going into this was that having an option to split streams and show them based on SD vs Auction would be a good idea to give participants an option to see certain streams based on what the question may ask, but many participants disregarded those options and just clicked the option that essentially created the static chart a second time even after being given interactive options. 
It is possible that either our questions were not a good set for evaluating the use of this filter, or that our chart wasn't the appropriate one for this filter. It is hard to tell which one is at fault for the uselessness of our filter; however, even with that uncertainty, we do know our static visualization is very strong, since participants opted to use the static option about twice. 
It would also be a valuable idea to run a few tests again on other interactive ideas for some of the other visualizations we have, because it's clear that, for this chart in particular, an interactive option is not plausible. It would also have been more beneficial to interview more than 10 people, just in case the numbers start to change around the 20- or 30-person mark. Another limitation would be prior familiarity with data visualizations and charts. 
The biggest limitation is that we tested only one visualization with one type of interaction, so our findings can't automatically be applied to all visualizations in our project. The questions we had were very strong, as evidenced by the times in our CSV file: none were done instantaneously, and none took over 5 minutes to answer for such simple visualizations. This meant our questions were reasonably challenging without being excessively difficult.
