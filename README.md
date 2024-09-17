# Experiment-4-ECE-2112
#### Objectives:
1. To identify the codes and functions needed in cleaning and visualizing data
2. To be able to apply and use the different codes and functions in creating a Python program that will be used in data wrangling and data visualization

## Problem 1:
#### Instructions:
1. Create the following data frames based on the format provided: Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas
_____
#### a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon
_____
For part a of Part 1 of Problem 1, the first step taken is to import the pandas library to be able to access its data managing functions:
- import pandas as pd

Next, I loaded the given file board2.xlsx (converted to .csv using excel) using the function pd.read_csv():
- a = pd.read_csv('board2.csv')

To get the Name, GEAS, and Electronics to appear based on the constants "Instrumentation" and "Luzon", I used the .loc[] function:
- Instru = a.loc[(a['Track'] == 'Instrumentation')& (a['Hometown'] == 'Luzon')& (a['Electronics'] > 70) , ['Name', 'GEAS', 'Electronics']]

The output I got was the Name, GEAS score, and Electronics score of the students who belong to the Instrumentation track and are from Luzon

___
#### b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female
___
Similar to problem a, problem b uses the same pandas function but with a few more steps:
- Mindy = a.loc[(a['Hometown'] == 'Mindanao')
        & (a['Gender'] == 'Female') 
        & ((((a['Math'])+(a['GEAS'])+(a['Electronics'])+(a['Communication']))/4) >= 55),
        ['Name', 'Track', 'Electronics']]

  First the parameters for the Hometown, and Gender were first set to the specific keywords. Next, I took the sum of the rows for the Math, GEAS, Electronics and Communication and divided it by 4 to manually obtain the mean. Afterwards, I used the "greater than or equal to" operation to get any averages greater than 55. </br>

  Next, I needed to get the column of averages. So I used the following lines of code:
- Mindy['Average'] = (((a['Math'])+(a['GEAS'])+(a['Electronics'])+(a['Communication']))/4)
- a['Average'] = (((a['Math'])+(a['GEAS'])+(a['Electronics'])+(a['Communication']))/4)

Finally, inputting Mindy prints the dataframe that contains the Names, Tracks, Electronics grades, and Averages of students who meet the parameters.

## Problem 2
#### Instructions: 
Create a visualization that shows how the different features contributes to average grade. Does
chosen track in college, gender, or hometown contributes to a higher average score?
___
For this problem, I imported matplotlib to be able to use the bar graphs:
- import matplotlib.pyplot as plt
Next, I put a to print out the entire dataframe with the Averages
- a
Finally I used plt.bar() 3 times, each for a different category with the averages remaining the same for all of them:
- plt.bar(a['Gender'], a['Average'])
- plt.bar(a['Track'], a['Average'])
- plt.bar(a['Hometown'], a['Average'])

From these bar graphs, the following seem to have a possible correlation with high grades
1. Gender = Females score higher
2. Track = Those who take Microelectronics score higher
3. Hometown = Those who are from Luzon score higher
