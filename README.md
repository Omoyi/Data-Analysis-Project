# **Uber Trip Data Analysis: A Power BI & Python Project**

### **1. Project Overview**

This project's goal was to perform a data analysis of a large Uber trip dataset. I used a combination of Python for initial data preparation and Power BI for creating a comprehensive, interactive dashboard. The report below summarizes my methodology, key findings, and the solutions to the technical challenges I faced along the way.

### **2. Tools Used**

* **Python (Jupyter Notebook, Matplotlib, Panda, and Seaborn libraries):** For initial data loading and preparation.
* **Power BI:** For visualization, dashboard design, and interactive analysis.

#### **3.1 Cloning Requirements**

1. Make sure you set up your environment and have all the tools I listed above.
2. Download the uber dataset from Kaggle: https://www.kaggle.com/datasets/yasserh/uber-fares-dataset
2. After forking or cloning this project first run the code in the first jupyter notebook because it is the only one in which I loaded the data frame. If you run other notebook segments before running the first you might get an error about the dataFrame not being defined.

### **3. Data Analysis & Visualization**

#### **3.1 Time-Based Analysis**

I first focused on understanding temporal patterns in the data.

* **Daily Ride Trends:** I created a bar chart to show ride volume by day of the week. This revealed a clear pattern: ride volume peaks on weekends, especially on **Fridays and Saturdays**, suggesting higher demand for social events.

    * *Screenshot:* ![Daily ride volume by day of the week.](/visualization/Day-peakHour.png)

* **Monthly & Seasonal Trends:** To understand seasonal patterns, I created a line chart. A key technical challenge was sorting the months correctly. I overcame this by creating a `month_sorting` column in Power Query and setting the `month` column to sort by it.

    * *Challenge:* ![Screenshot showing sorting issue with months.](/visualization/Sorting%20issue.png)

    * *Solution:* ![Screenshot showing the month sorting column.](/visualization/sort-columns.png)

    The final, sorted chart revealed a significant peak in ride volume during the **spring months (March to May)**. This led me to hypothesize that favorable weather during this season drives an increase in demand. I enhanced the visual by creating a `Season` column and adding it to the chart's legend.

    * *Final Visual:* ![Monthly ride volume with season legend.](/visualization/weatherTrends.png)

#### **3.2 Fare & Trip Patterns**

* **Fare vs. Distance:** I created a scatter plot to analyze the relationship between `fare_amount` and `distance_km`. I initially faced an issue where the chart showed only one dot because Power BI was aggregating the data. The solution was switch to a line plot The final chart showed a strong, positive linear correlation, confirming that fare is directly tied to distance.

    * *Python:* ![Screenshot of generated scatter plot in Python.](/visualization/fare_distance.png)

    * *Solution:* ![Screenshot of the Line plot and changing to "Do not summarize".](/visualization/fare-distance.png)

* **Fare vs. Passenger Count:** A bar chart comparing average fare by `passenger_count` produced a surprising result: the average fare for more than 2 passengers was unusually low and almost non-existent. I investigated this by creating a second chart showing the count of trips per passenger. This revealed that the number of trips with 2 passengers was extremely low, making the average highly unreliable. 

    * *Challenge:* ![Screenshot of average fare by passenger count with an unusual result.](/visualization/passenger-count.png)

    * *Solution:* ![Screenshot of the count of trips by passenger count.](/visualization/Fare-passenger.png)

#### **3.3 Geographic Distribution**

To understand where trips were happening, I used a map visualization. Initially, the map showed a single dot. The fix was the same as the scatter plot: I had to set the `latitude` and `longitude` fields to **"Don't summarize"**. The final map showed a dense cluster of rides in a specific area.

* *Final Visual:* ![Screenshot of map showing ride paths in a specific area.](/visualization/Map.png)

### **4. Key Findings**

* Ride demand is highest on weekends and during the spring season.
* Fare is strongly correlated with trip distance.
* The business operates primarily within North America.
* The most profitable trips (long and expensive) occur during specific daily timeframes (9 AM - 10 PM).

### **5. Conclusion & Recommendations**

This analysis provides a clear picture of the company's operational patterns. To capitalize on these findings, I would recommend implementing dynamic pricing during peak demand times (weekends and evenings), offering incentives for drivers to operate in busy areas and during peak seasons, and exploring marketing campaigns to increase ridership during slower periods.

### **6. Dashboard Interactivity**

To make the dashboard fully interactive, I added slicers for `day_of_week` and `month`. This allows users to filter the data and gain their own insights. All charts were also formatted for a professional and consistent look.