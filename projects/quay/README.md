# **CS7290 Final Project**

Author: Quay Dragon

I worked with Ian Dardik on this project. We decided to create separate models 

## **Introduction**

## **Updates since the final presentation**

1. Updated the greedy algorithm comparison for every year. 
2. Added mean squared error. 

## **Data**

Here is the sequence of steps I took to scrape and clean the data:

(From Ian)

1. I manually copied and pasted the data from [here](https://www.pro-football-reference.com/years/2020/rushing.htm) using the "Share & Export" -> "Get table as CSV (for Excel)" option.
2. I copied the past 20 years of data into a single file called [raw_data.csv](https://github.com/iandardik/CS7290_project/blob/master/raw_data.csv)
3. I then cleaned up a few random characters of raw_data.csv using the "sed" linux program (see the exact commands [here](https://github.com/iandardik/CS7290_project/blob/master/clean_commands.txt)).
4. I then used a python script to add the "Next Year" columns, i.e. stats such as Attempts and Points that each player will score in the subsequent year. Here is the [script](https://github.com/iandardik/CS7290_project/blob/master/kv_data.py). This script outputs a file called [data.csv](https://github.com/iandardik/CS7290_project/blob/master/data.csv).
5. All of my Jupyter notebooks use data.csv from my github repository and perform additional clean up to the data. The additional clean up is covered in the notebooks themselves.

I will also note that it was helpful to visualize the data in excel using [this file](https://github.com/iandardik/CS7290_project/blob/master/data_analysis.xlsx).

Quay Processing:

1. Cleaned the positions of the model.
2. Creating 10 buckets of players for their different skill levels.

## **Models**

The below notebook contains the prior, posterior, and loss analysis as well as the youtube video explaining the project.

1. [https://colab.research.google.com/drive/1b8IarxD6pIfzBJQtlRhLo55DPnEvU0ky#scrollTo=2Xk4bjePn3Sp](https://colab.research.google.com/drive/1b8IarxD6pIfzBJQtlRhLo55DPnEvU0ky#scrollTo=2Xk4bjePn3Sp)
2. [https://www.youtube.com/watch?v=3EyV_B_RUFs](https://www.youtube.com/watch?v=3EyV_B_RUFs)

## **Results**

Compared to the greedy algorithm the model showed a <100 average loss year over year. The greedy algorithm consists of picking the top players from the previous year and placing them in the greedy opponents line up. The draft is done by allowing my algorithm to pick first and then the greedy algorithm. However, not better than the greedy algorithm on average the model still attains reasonable results for a fantasy football pool. Next we check mean squared error. The mean squared error was 2611.4991. This is is consistent with the below 100 loss rate.

## **Discussion**

The algorithm performs well on the players in the ranking bucket 0 - 8. This means when filling your fantasy football team discretion should still be used for the highest ranking players. There may be news surrounding these player which would be helpful in choosing them. The algorithm works by first bucketing the players into 10 different groups. Assessing the attempts each player is likely to make in a season and using that to project yards, TDs, and fumbles. These are then put into the point function. The attempts model is the most important model in this hierarchal model because of the impact it has on each preceding model. Outliers are extremely hard to predict because of their own randomness. 

## **Conclusion**

If I was to enter a fantasy football pool without any real knowledge about the game I would certainly be using the model to pick players. Due to the average being worse than greedy at times I would make sure to check for outliers in the data. The model performs poorly on the outlier data even with a wider tailed distribution. The model should be used as a guideline to pick players while using discretion if some players are known to be very good.