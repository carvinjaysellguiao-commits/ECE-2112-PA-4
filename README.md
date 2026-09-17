# ECE-2112-PA-4
Made by Carvin Jaysell D. Guiao | 2ECE-D
<br>
This programming assignment focuses on using Pandas and a Python plotting library within a Jupyter Notebook environment. It explains that the task involves working with datasets and performing data analysis and visualization using Python tools.

## Set Up
```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_excel("board2.xlsx")
df.head()
```

This cell imports the required libraries using ``import pandas as pd`` and ``import matplotlib.pyplot as plt``. Pandas is used for handling and analyzing tabular data, while Matplotlib is used for creating visualizations such as bar charts. The following cell loads the dataset using ``pd.read_excel()`` and stores it in the DataFrame ``df``. The function ``df.head()`` is used to display the first few rows to verify that the data and column names are correctly loaded.

## A. Visayas Communication Dataframe
This problem focuses on applying multiple logical conditions to isolate a specific subset of student records. In this problem, we are tasked with filtering the dataset for Visayas students in the communication track, retaining only the five specific columns, and displaying the resulting DataFrame with its row count.
```python
VisComm = df[
    (df["Hometown"] == "Visayas") &
    (df["Track"] == "Communication")
][["Name", "Gender", "Math", "Electronics", "Average"]]

print(VisComm)
print("Number of rows:", len(VisComm))
```
This cell filters the dataset using conditions with ``(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")``. It then selects specific columns using double brackets ``[[...]]`` to create the ``VisComm`` DataFrame. The results are displayed using ``print()`` and counted using ``len()``.
## B. Visayas Female Dataframe
This task demonstrates two-step data wrangling by first generating a secondary filtered DataFrame based on demographic criteria and subsequently applying a numerical threshold without altering the main subject. We are tasked with extracting female students from Visayas into a ``VisFemale`` DataFrame with specified columns and displaying a secondary filtered view of records where ``Average`` is at least 60 without altering the original subset.
```python
VisFemale = df[
    (df["Hometown"] == "Visayas") &
    (df["Gender"] == "Female")
][["Name", "Track", "GEAS", "Electronics", "Average"]]

print(VisFemale)
```
This cell creates the VisFemale DataFrame by filtering with ``(df["Hometown"] == "Visayas") & (df["Gender"] == "Female")``. It keeps only selected columns using column indexing with ``[[...]]``. The resulting DataFrame is displayed using ``print()``.
```python
VisFemale_60 = VisFemale[VisFemale["Average"] >= 60]
print(VisFemale_60)
```
This cell applies an additional condition using ``VisFemale["Average"] >= 60`` to filter the data. The result is stored in a new DataFrame ``VisFemale_60`` to avoid modifying the original.

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
This cell computes group averages using ``groupby()`` and ``mean()`` on the column <b>"Average"</b>. It creates summaries for <b>Track, Gender, and Hometown</b> stored in separate variables.

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

```python
print("1. The track with the highest average score is ", track_avg.idxmax())
print("2. The gender with the highest average score is ", gender_avg.idxmax())
print("3. The hometown group with the highest average score is ", hometown_avg.idxmax())
```
This cell identifies the category with the highest average score for each of the three features: <b>Track, Gender, and Hometown</b>. The ``idxmax()`` function is used to determine which category has the maximum mean value.
<br>
<br>
Thank you for reading!
<br>
To check and download the notebook output, kindly click [Programming Assignment 4](http://localhost:8888/files/Programming%20Assignments/Programming%20Assignment%204_GUIAO%2CCJ.ipynb?_xsrf=2%7C45e55d6c%7Cc0efecbc3aedd362b8d648a0636eb402%7C1789647780). Thank you!

#### README Version History
<br>
September 15, 2026 - README Upload and Draft
<br>
September 15, 2026 - Update
<br>
September 16, 2026 - Finalization and Notebook Upload
