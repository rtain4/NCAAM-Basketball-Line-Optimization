# NCAAM-Basketball-Line-Optimization
This tool helps identify the most optimal 5-man lineup for a selected NCAA men’s basketball team (Team A) to face another team (Team B), based on individual player matchups and statistical strengths vs. weaknesses.\

Coaches and general managers often face the challenge of determining the most effective five-player lineup on the court at any given time. This involves understanding individual player strengths and weaknesses, how they complement or contradict each other, and how to best exploit the opponent's vulnerabilities. Traditional scouting relies heavily on observation and subjective analysis. This tool aims to provide a more objective and data-driven approach to lineup selection.

What data was used and how was it sourced?

The primary data source for this tool is advanced college basketball statistics from barttorvik.com. Specifically, the tool uses player statistics from the 2023-2024 and 2024-2025 seasons. The data is sourced directly from the provided CSV URLs:

https://barttorvik.com/getadvstats.php?year=2024&csv=1 (for the 2023-2024 season)
https://barttorvik.com/getadvstats.php?year=2025&csv=1 (for the 2024-2025 season)
The data is retrieved using the requests library in Python, and then loaded into pandas DataFrames for processing. A separate Excel file (pstatheaders.xlsx) is used to provide the correct column headers for the imported CSV data.

How was the solution built (tools, libraries, languages)?

The solution is built using Python within a Google Colaboratory or Jupyter Notebook environment. Key libraries used include:

pandas: For data manipulation, loading, cleaning, and analysis.
requests: To fetch the data from the provided URLs.
BeautifulSoup: Although imported in the provided code, it is not actively used in the final version of the tool for data extraction, as the data is directly available in CSV format.
io: To read the fetched CSV data into a format pandas can process.
sklearn.preprocessing.StandardScaler: To standardize the player statistics for clustering.
sklearn.cluster.KMeans: To perform K-Means clustering to group players into roles.
matplotlib.pyplot: To generate visualizations of player role and weakness distributions.
itertools.combinations: To generate all possible 5-player lineup combinations for optimization.
IPython.display and ipywidgets: To create an interactive user interface within the notebook for selecting teams and seasons.
The core logic of the solution involves:

Data Acquisition and Cleaning: Loading player statistics and handling missing values.
Player Clustering: Applying K-Means clustering to group players based on their advanced statistics, assigning them to distinct "role clusters."
Role Naming and Categorization: Analyzing the statistical characteristics of each cluster to assign general "role names" (e.g., "Star Player," "Bench Player") and more specific "role categories" (e.g., "3P Sharp Shooter," "Slasher").
Weakness Mapping: Identifying and listing key statistical weaknesses for each player based on defined thresholds (e.g., high turnover percentage, poor free throw shooting).
Lineup Optimization:
The evaluate_lineup function calculates a score for a given 5-player lineup against an opponent by assessing how well the players in the lineup statistically counter the weaknesses of the opposing players.
The find_optimal_lineup function iterates through all possible 5-player combinations from a team's roster and uses evaluate_lineup to determine the combination with the highest score against the specified opponent.
Interactive User Interface: Using ipywidgets to create dropdown menus for selecting seasons and teams, and a button to trigger the lineup optimization and display the results and relevant charts.
Why is it useful to a General Manager or Coaching Staff?

This tool provides valuable insights for General Managers and Coaching Staff by:

Objective Player Evaluation: It offers a data-driven method to categorize players into distinct roles and identify their statistical weaknesses, supplementing traditional scouting reports.
Strategic Lineup Planning: It suggests optimal 5-player lineups specifically tailored to exploit an opponent's weaknesses, allowing coaches to make more informed decisions during game planning and in-game adjustments.
Understanding Team Composition: The role and weakness distribution charts visualize the overall strengths and weaknesses of a team's roster, which can inform recruitment and player development strategies.
Efficiency and Time Saving: Automating the process of evaluating countless lineup combinations significantly reduces the time and effort required compared to manual analysis.
By providing a quantitative basis for lineup decisions and player analysis, this tool empowers basketball personnel to enhance their strategic approach and potentially gain a competitive edge.
