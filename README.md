Week 6 Assignment

# Python-API-Challenge

The Python-API-Challenge will harness the capabilites of Python, APIs, and JSON traversals to explore the fundamental question: "What is the weather like as we approach the equator?"


## Prerequisites

Before working on the Python-API-Challenge, ensure you complete the following requirements:

-  Install VS Code and Python on your machine with the Pandas and Hyplot libraries OR install Jupyter notebooks with the geoViews library. 

- Two API keys: OpenWeatherAPI and geoViews API. 

- Create a new repository called 'python-api-challenge' in GitHub with  README and .gitignore files


## Repository Setup

Repository Setup:
  - Create a new repository called 'python-api-challenge' in GitHub with a README file
  - Copy the SSH key in GitHub
  - Open the Git Bash terminal mkdir a folder called 'python-api-challenge'
  - Navigate into the directory 
  - Clone SSH key in directory
  - Create two directories named 'WeatherPy' and 'VacationPy' and download the starter code files in both directories. 
  - Add .gitignore file to prevent sensitive information like your API keys from being pushed to GitHub.
  - Git add, commit, and push changes into the repository.

```
Example:
mkdir 'python-api-challenge'
cd python-api-challenge
mkdir 'WeatherPy' and 'VacationPy' 
git add .
git commit -m "Pushing challenge work"
git push 
```


## Adding a .gitignore File

1. Open your python-api-challenge GitHub folder in VS Code.
2. Create a .gitignore file and add the following line to it:

```
api_keys.py
```
3. Check the status of your files:
```
git status
```
4. Add and commit the necessary files:
```
git add .gitignore WeatherPy.ipynb VacationPy.ipynb
git commit -m "Initial commit with .gitignore and notebook files"
git push origin main
```


## Instructions

Ensure you have downloaded both starter code files to start the challenge..


The challenge is separated into two parts:

 - WeatherPy

 - VacationPy


PART 1: WeatherPy

Create a Python script to visualize the weather of over 500 cities at varying distances from the equator. Use the citipy library, the OpenWeatherMap API, and your problem-solving skills to model the weather across different cities.

Steps:

1. Retrieve Weather Data: Use the OpenWeatherMap API to fetch weather data for the cities list.
2. Create Plots: Create scatter plots to visualize the following relationships for the Northern and Southern Hemispheres:
  - Latitude vs. Temperature
  - Latitude vs. Humidity
  - Latitude vs. Cloudiness
  - Latitude vs. Wind Speed
3. Linear Regression: Compute and visualize the linear regression for each relationship above, separating the data into Northern and Southern Hemispheres.
 

PART 2: VacationPy

Use the weather data to plan vacations and create map visualizations using Jupyter notebooks, the geoViews library, and the Geoapify API.

Steps:

1. Display City Points: Create a map displaying a point for every city in the ``` city_data_df ``` DataFrame, with point size representing the humidity.
2. Filter Ideal Weather Conditions: Narrow the ``` city_data_df ``` to those meeting ideal weather conditions (e.g., temperature, wind speed, cloudiness).
3. Find Hotels: Create a new DataFrame called ``` hotel_df ```. Use the Geoapify API to locate the first hotel within 10,000 meters of each city’s coordinates.
4. Create Hover Messages: Add hotel names and countries to each city's hover messages on the map.


## WeatherPy Script Example 

```VS Code
-- Create a Scatter Plot for Latitude Vs. Temperature 

# Build scatter plot for latitude vs. temperature
plt.figure(figsize=(8,5))
plt.scatter(city_data_df['Lat'], city_data_df['Max Temp'], edgecolors='black', alpha=0.70)
plt.title("City Max Latitude vs. Temperature (2024-6-19)")
plt.xlabel("Latitude")
plt.ylabel("Max Temperature (C)")
plt.grid(True)

# Save the figure
output_dir = "output_file"
if not os.path.exists(output_dir):
    os.makedirs(output_dir)
output_data = os.path.join(output_dir, "Fig1.png")

plt.savefig(output_data)

#Show plot
plt.show()
```


## VacationPy Script Example

```VS Code
-- Step 1: Create a map that displays a point for every city in the `city_data_df` DataFrame. The size of the point should be the humidity in each city.

%%capture --no-display

output_dir = 'output_data'
if not os.path.exists(output_dir):
    os.makedirs(output_dir)

# Configure the map plot
humidity_map = city_data_df.hvplot.points(
    'Lng',
    'Lat',
    geo = True,
    titles = 'OSM',
    frame_width = 800,
    frame_height = 600,
    size = 'Humidity',
    scale = 1,
    color = 'City'
)

# Display the map
hvplot.save(humidity_map, os.path.join(output_dir, 'humidity_map.html'))
humidity_map
```


## Acknowledgements

I want to mention the following individuals and resources for their assistance and support throughout this assignment: 
- Class instructor Elias and Class TA Brian
- AskBCS Learning Assistant 
- Xpert Learning Assistant and ChatGPT