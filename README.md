# Marquez Experiment #4
# DATA WRANGLING AND DATA VISUALIZATION

## Learning Intended Outcomes: 
1. To identify the codes and functions needed in cleaning and visualizing data
2. To be able to apply and use the different codes and functions in creating a Python program that will be used in data wrangling and data visualization

## Preparation for the Experiment
The creator downloaded the xlsx file named 'board2.xlsx' for the proper demonstration of data wrangling and visualization

# ECE BOARD EXAM PROBLEM
Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

## Primary Instruction/Question:
1. Create the following data frames based on the format provided
2. Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?

## Procedures:

## Creating the Data Frame using the Provided Format
### Importing Pandas Library for Creating the Data Frame
```python
#Start of Code
import pandas as pd
```
### Loading the Excel data in the Notebook
```python
#Importing the Board2 Excel data
board  = pd.read_excel("board2.xlsx")
board
```
| Name | Gender | Track            | Hometown | Math | Electronics | GEAS | Communication |
|------|--------|------------------|----------|------|-------------|------|---------------|
| S1   | Male   | Instrumentation  | Luzon    | 58   | 89          | 75   | 78            |
| S2   | Female | Communication    | Mindanao | 52   | 75          | 90   | 52            |
| S3   | Female | Instrumentation  | Mindanao | 83   | 74          | 77   | 57            |
| S4   | Male   | Instrumentation  | Visayas  | 65   | 58          | 91   | 68            |
| S5   | Male   | Communication    | Luzon    | 59   | 86          | 43   | 88            |
| S6   | Female | Microelectronics | Visayas  | 88   | 45          | 86   | 83            |
| S7   | Female | Instrumentation  | Luzon    | 66   | 60          | 60   | 48            |
| S8   | Male   | Instrumentation  | Luzon    | 49   | 81          | 64   | 53            |
| S9   | Male   | Instrumentation  | Luzon    | 50   | 36          | 63   | 42            |
| S10  | Male   | Microelectronics | Mindanao | 80   | 84          | 61   | 44            |
| S11  | Female | Communication    | Visayas  | 48   | 56          | 48   | 67            |
| S12  | Male   | Communication    | Visayas  | 89   | 67          | 84   | 64            |
| S13  | Female | Microelectronics | Luzon    | 88   | 35          | 83   | 43            |
| S14  | Female | Microelectronics | Luzon    | 83   | 77          | 89   | 73            |
| S15  | Female | Microelectronics | Mindanao | 69   | 41          | 40   | 86            |
| S16  | Female | Communication    | Luzon    | 71   | 70          | 87   | 81            |
| S17  | Female | Microelectronics | Mindanao | 81   | 79          | 77   | 45            |
| S18  | Male   | Communication    | Visayas  | 81   | 40          | 81   | 52            |
| S19  | Male   | Microelectronics | Luzon    | 79   | 63          | 79   | 71            |
| S20  | Female | Communication    | Mindanao | 59   | 60          | 62   | 85            |
| S21  | Female | Microelectronics | Visayas  | 83   | 51          | 68   | 72            |
| S22  | Female | Communication    | Visayas  | 64   | 39          | 89   | 58            |
| S23  | Male   | Instrumentation  | Luzon    | 84   | 70          | 74   | 47            |
| S24  | Female | Microelectronics | Visayas  | 85   | 45          | 60   | 41            |
| S25  | Male   | Communication    | Luzon    | 74   | 91          | 94   | 42            |
| S26  | Female | Instrumentation  | Visayas  | 71   | 47          | 83   | 62            |
| S27  | Male   | Microelectronics | Visayas  | 70   | 47          | 40   | 86            |
| S28  | Male   | Communication    | Visayas  | 85   | 53          | 80   | 53            |
| S29  | Male   | Instrumentation  | Mindanao | 73   | 48          | 71   | 62            |
| S30  | Male   | Instrumentation  | Luzon    | 78   | 81          | 57   | 56            |

### Part a. Instru
Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon

-Using Indexing to get the specific columns needed
```python
#Using Indexing to filter specific columns and set a condition to a given data
partA = board.loc[(board['Hometown'] == 'Luzon')
                & (board['Track'] == 'Instrumentation') 
                & (board['Electronics'] > 70)]
```

-Placing the partA in a variable named 'Instru'
```python
#Place it in the variable named 'Instru'
Instru = partA[['Name','GEAS','Electronics']]
Instru
```
| Name | GEAS | Electronics |
|------|------|-------------|
| S1   | 75   | 89          |
| S8   | 64   | 81          |
| S30  | 57   | 81          |

### Part b. Mindy
Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

-Adding an Average data for all the scores of every students using .mean
```python
#Adding an average data column by getting the mean from different categories
board['Average'] = board[['Electronics', 'GEAS', 'Math', 'Communication']].mean(axis=1)
```

-Primary Extracting Tool: INDEXING
```python
#Using Indexing to filter specific columns and set a condition to a given data
partB = board.loc[(board['Hometown'] == 'Mindanao')
                & (board['Gender'] == 'Female')
                & (board['Average'] >= 55)]
```

-Placing the partA in a variable named 'Instru'
```python
#Place it in the variable named 'Instru'
Mindy = partB[['Name','Track','Electronics', 'Average']]
Mindy
```

| Name | Track            | Electronics | Average |
|------|------------------|-------------|---------|
| S2   | Communication    | 75          | 67.25   |
| S3   | Instrumentation  | 74          | 72.75   |
| S15  | Microelectronics | 41          | 59.00   |
| S17  | Microelectronics | 79          | 70.50   |
| S20  | Communication    | 60          | 66.50   |


## Creating Visualization
### Importing Matplot Library
```python
#Importing matplotlib
import matplotlib.pyplot as plt
```

### Importing Seaborn Library
```python
#Importing matplotlib
import seaborn as sns
```

### Loading the Excel data in the Notebook
```python
#Importing the Board2 Excel data
board  = pd.read_excel("board2.xlsx")
board
```
| Name | Gender | Track            | Hometown | Math | Electronics | GEAS | Communication |
|------|--------|------------------|----------|------|-------------|------|---------------|
| S1   | Male   | Instrumentation  | Luzon    | 58   | 89          | 75   | 78            |
| S2   | Female | Communication    | Mindanao | 52   | 75          | 90   | 52            |
| S3   | Female | Instrumentation  | Mindanao | 83   | 74          | 77   | 57            |
| S4   | Male   | Instrumentation  | Visayas  | 65   | 58          | 91   | 68            |
| S5   | Male   | Communication    | Luzon    | 59   | 86          | 43   | 88            |
| S6   | Female | Microelectronics | Visayas  | 88   | 45          | 86   | 83            |
| S7   | Female | Instrumentation  | Luzon    | 66   | 60          | 60   | 48            |
| S8   | Male   | Instrumentation  | Luzon    | 49   | 81          | 64   | 53            |
| S9   | Male   | Instrumentation  | Luzon    | 50   | 36          | 63   | 42            |
| S10  | Male   | Microelectronics | Mindanao | 80   | 84          | 61   | 44            |
| S11  | Female | Communication    | Visayas  | 48   | 56          | 48   | 67            |
| S12  | Male   | Communication    | Visayas  | 89   | 67          | 84   | 64            |
| S13  | Female | Microelectronics | Luzon    | 88   | 35          | 83   | 43            |
| S14  | Female | Microelectronics | Luzon    | 83   | 77          | 89   | 73            |
| S15  | Female | Microelectronics | Mindanao | 69   | 41          | 40   | 86            |
| S16  | Female | Communication    | Luzon    | 71   | 70          | 87   | 81            |
| S17  | Female | Microelectronics | Mindanao | 81   | 79          | 77   | 45            |
| S18  | Male   | Communication    | Visayas  | 81   | 40          | 81   | 52            |
| S19  | Male   | Microelectronics | Luzon    | 79   | 63          | 79   | 71            |
| S20  | Female | Communication    | Mindanao | 59   | 60          | 62   | 85            |
| S21  | Female | Microelectronics | Visayas  | 83   | 51          | 68   | 72            |
| S22  | Female | Communication    | Visayas  | 64   | 39          | 89   | 58            |
| S23  | Male   | Instrumentation  | Luzon    | 84   | 70          | 74   | 47            |
| S24  | Female | Microelectronics | Visayas  | 85   | 45          | 60   | 41            |
| S25  | Male   | Communication    | Luzon    | 74   | 91          | 94   | 42            |
| S26  | Female | Instrumentation  | Visayas  | 71   | 47          | 83   | 62            |
| S27  | Male   | Microelectronics | Visayas  | 70   | 47          | 40   | 86            |
| S28  | Male   | Communication    | Visayas  | 85   | 53          | 80   | 53            |
| S29  | Male   | Instrumentation  | Mindanao | 73   | 48          | 71   | 62            |
| S30  | Male   | Instrumentation  | Luzon    | 78   | 81          | 57   | 56            |

### Adding the Average Column
-Using the .mean to get the average of one student in every category
```python
#Adding the Average
board['Average'] = board[['Math', 'Electronics', 'Communication','GEAS']].mean(axis=1)
```

### Using Bar Graph
-Bar Graph is one of the most optimal way to visualize and compare sets of data
```python
#Setting up the overall size of the graph
plt.figure(figsize=(25,13))

#Using the subplot to have the three sets of arguments combined in one ordered line

#Track-Average Graph
plt.subplot(1, 3, 1)
plt.title('Average Grades Categorized by College Track')
sns.barplot(x='Track', y='Average', data=board, errorbar=None) #Utilized to label the x & y axis by their corresponding variable

#Gender-Average Graph
plt.subplot(1, 3, 2)
plt.title('Average Grades Categorized by Gender')
sns.barplot(x='Gender', y='Average', data=board, errorbar=None) #Utilized to label the x & y axis by their corresponding variable

#Hometown-Average Graph
plt.subplot(1, 3, 3)
plt.title('Average Grades Categorized by Hometown')
sns.barplot(x='Hometown', y='Average', data=board, errorbar=None) #Utilized to label the x & y axis by their corresponding variable
```
![BarGraph_E4](https://github.com/user-attachments/assets/85fc6d45-cb16-4949-8d8e-c0c15f5f588b)

```python
#End of Code
```

## Data Analysis

### Main Question
Does chosen track in college, gender, or hometown contributes to a higher average score?

### College Track
Looking at the graph above, we can see that there is a minimal but noticeable difference between the average of the different tracks. The track with the highest average is the 'Communications', while the the track with the lowest average is the 'Instrumentation' track.

### Gender
Similarly, there is a minimal difference between the average of males and females. Looking at the data, the male group has the higher average grade by a very small margin.

### Hometown
Based on the graph above, we can see that the Luzon group has the highest average grade, followed by Mindanao and then Visayas. The difference wasn't significant enough to conclude any strong correlation.

## Conclusion
There were some discrepancies between each category, but the differences were minimal, thus concluding that there's insufficient evidence to claim a strong correlation.
