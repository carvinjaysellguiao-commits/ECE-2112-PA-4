# ECE-2112-PA-4
Made by Carvin Jaysell D. Guiao | 2ECE-D
<br>
This programming assignment focuses on datasets using Pandas and a Python plotting library in Jupyter Notebook.

## Set Up
```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_excel("board2.xlsx")
df.head()
```

## A. Visayas Communication Dataframe
This problem focuses on applying multiple logical conditions to isolate a specific subset of student records. In this problem, we are tasked to filter the datasets for Visayas students in the communication track, retaining only the five specific columns, and display the resulting DataFrame with its row count.
```python
VisComm = df[
    (df["Hometown"] == "Visayas") &
    (df["Track"] == "Communication")
][["Name", "Gender", "Math", "Electronics", "Average"]]

print(VisComm)
print("Number of rows:", len(VisComm))
```

## B. Visayas Female Dataframe
This task demonstrates two-steps data wrangling by first generating a secondary filtered DataFrame based on demographic criteria and subsequently applying numerical threshold without altering the main subject. We are tasked to extract female students from Visayas into a ``VisFemale`` DataFrame with specified column and display a secondary filtered view of records where ``Average`` is at least 60 without altering the original subset.
```python
VisFemale = df[
    (df["Hometown"] == "Visayas") &
    (df["Gender"] == "Female")
][["Name", "Track", "GEAS", "Electronics", "Average"]]

print(VisFemale)
```

```python
VisFemale_60 = VisFemale[VisFemale["Average"] >= 60]
print(VisFemale_60)
```

## C. Category-Average Visualization
This section deals with exploratory data analysis and data visualization, aggregating board exam averages across different demographic and academic categories to present comparative insights visually. We are required to calculate the summary tables for the mean ``Average`` across Track, Gender, and Hometown - plot these in a three-bar-chart figure and state the highest sample mean category for each feature.
```python
track_avg = df.groupby("Track")["Average"].mean()
gender_avg = df.groupby("Gender")["Average"].mean()
hometown_avg = df.groupby("Hometown")["Average"].mean()

print(track_avg)
print(gender_avg)
print(hometown_avg)
```


```python
plt.figure(figsize=(12, 4))
```
This code creates a new figure canvas using Matplotlib with a specified size of 12 inches in width and 4 inches in height. It sets the overall layout space where all subplots will be displayed side by side.

```python
plt.subplot(1, 3, 1)
track_avg.plot(kind='bar')
plt.title("Average by Track")
plt.xlabel("Track")
plt.ylabel("Average")
```
This code creates the first subplot in a 1-row, 3-column layout and plots a bar chart of ``track_avg``. It displays the average values grouped by track and labels the axes for clear interpretation.

```python
plt.subplot(1, 3, 2)
gender_avg.plot(kind='bar')
plt.title("Average by Gender")
plt.xlabel("Gender")
plt.ylabel("Average")
```
This code creates the second subplot in the same figure and generates a bar chart for ``gender_avg``. It shows the comparison of average values across different gender categories.
```python
plt.subplot(1, 3, 3)
hometown_avg.plot(kind='bar')
plt.title("Average by Hometown")
plt.xlabel("Hometown")
plt.ylabel("Average")
```
This code creates the third subplot and plots a bar chart of ``hometown_avg``. It visualizes how averages vary across different hometowns.

```python
plt.tight_layout()
plt.show()
```
This code automatically adjusts spacing between subplots and displays the complete figure. It ensures that titles, labels, and plots do not overlap and are clearly visible.

<br>
Thank you for reading!
To check the notebook output, kindly click [here](). Thank you!

#### README Version History
<br>
September 15, 2026 - README Upload and Draft
<br>
September 15, 2026 - Update
