# "Data Analysis Assignment" 

When forking or downloading remember to run from the first jupyter notebook, because it is the one that has the data frame loaded. Without doing that before running other notebook segments you might get an error on the dataFrame not being defined.

# **Uber Trip Data Analysis: A Power BI & Python Project**

### **1. Project Overview**

This project's goal was to perform an in-depth analysis of a large Uber trip dataset. I used a combination of Python for initial data preparation and Power BI for creating a comprehensive, interactive dashboard. The report below summarizes my methodology, key findings, and the solutions to the technical challenges I faced along the way.

### **2. Tools Used**

* **Python (Jupyter Notebook):** For initial data loading and preparation.
* **Power BI:** For visualization, dashboard design, and interactive analysis.

### **3. Data Analysis & Visualization**

#### **3.1 Time-Based Analysis**

I first focused on understanding temporal patterns in the data.

* **Daily Ride Trends:** I created a bar chart to show ride volume by day of the week. This revealed a clear pattern: ride volume peaks on weekends, especially on **Fridays and Saturdays**, suggesting higher demand for social events.

    * *Screenshot:* ![Daily ride volume by day of the week.](/visualization/Day-peakHour.png)

* **Monthly & Seasonal Trends:** To understand seasonal patterns, I created a line chart. A key technical challenge was sorting the months correctly. I overcame this by creating a `month_sorting` column in Power Query and setting the `month` column to sort by it.

    * *Challenge:* ![Screenshot showing sorting issue with months.](/visualization/weatherTrends.png)

    * *Solution:* ![Screenshot showing the month sorting column.](_insert_link_to_screenshot_of_month_sorting_column_here_)

    The final, sorted chart revealed a significant peak in ride volume during the **spring months (March to May)**. This led me to hypothesize that favorable weather during this season drives an increase in demand. I enhanced the visual by creating a `Season` column and adding it to the chart's legend.

    * *Final Visual:* ![Monthly ride volume with season legend.](/visualization/weatherTrends.png)

#### **3.2 Fare & Trip Patterns**

* **Fare vs. Distance:** I created a scatter plot to analyze the relationship between `fare_amount` and `distance_km`. I initially faced an issue where the chart showed only one dot because Power BI was aggregating the data. The solution was to set both fields to **"Do not summarize."** The final chart showed a strong, positive linear correlation, confirming that fare is directly tied to distance.

    * *Challenge:* ![Screenshot of a scatter plot showing only one dot.](_insert_link_to_screenshot_of_single_dot_scatter_plot_here_)

    * *Solution:* ![Screenshot of the scatter plot after changing to "Do not summarize".](_insert_link_to_screenshot_of_correct_scatter_plot_here_)

* **Fare vs. Passenger Count:** A bar chart comparing average fare by `passenger_count` produced a surprising result: the average fare for 2 passengers was unusually low. I investigated this by creating a second chart showing the count of trips per passenger. This revealed that the number of trips with 2 passengers was extremely low, making the average highly unreliable. This highlighted the importance of checking data quality and sample size.

    * *Challenge:* ![Screenshot of average fare by passenger count with an unusual result.](_insert_link_to_screenshot_of_complicated_bar_chart_here_)

    * *Solution:* ![Screenshot of the count of trips by passenger count.](_insert_link_to_screenshot_of_trip_count_bar_chart_here_)

#### **3.3 Geographic Distribution**

To understand where trips were happening, I used a map visualization. Initially, the map showed a single dot. The fix was the same as the scatter plot: I had to set the `latitude` and `longitude` fields to **"Don't summarize"**. The final map showed a dense cluster of rides in a specific area.

* *Final Visual:* ![Screenshot of map showing ride paths in a specific area.](_insert_link_to_screenshot_of_final_map_here_)

### **4. Key Findings**

* Ride demand is highest on weekends and during the spring season.
* Fare is strongly correlated with trip distance.
* The business operates primarily within a concentrated geographic region.
* The most profitable trips (long and expensive) occur during specific daily timeframes (9 AM - 10 PM).

### **5. Conclusion & Recommendations**

This analysis provides a clear picture of the company's operational patterns. To capitalize on these findings, I would recommend implementing dynamic pricing during peak demand times (weekends and evenings), offering incentives for drivers to operate in busy areas and during peak seasons, and exploring marketing campaigns to increase ridership during slower periods.

### **6. Dashboard Interactivity**

To make the dashboard fully interactive, I added slicers for `day_of_week`, `month`, and `hour`. This allows users to filter the data and gain their own insights. All charts were also formatted for a professional and consistent look.