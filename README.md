# Surfs Up

## Projec Summary and Background
W. Avy likes your analysis, but he wants more information about temperature trends before opening the surf shop. Specifically, he wants temperature data for the months of June and December in Oahu, in order to determine if the surf and ice cream shop business is sustainable year-round.

## What You're Creating

> This new assignment consists of two technical analysis deliverables and a written report. You will submit the following:

1. ***Deliverable 1***: Determine the Summary Statistics for June
2. ***Deliverable 2***: Determine the Summary Statistics for December
3. ***Deliverable 3***: A written report for the statistical analysis [`README.md`](https://github.com/emmanuelmartinezs/surfs_up). 

## Resources and Before Start Notes:

* Data Source: `SurfsUp_Challenge_starter_code.ipynb` named later as `SurfsUp_Challenge.ipynb`
* Data File: `hawaii.sqlite`
* Software: Matplotli 3.2.2, Python 3.9, Visual Studio Code 1.50.0, Anaconda 4.8.5, Jupyter Notebook 6.1.4, Pandas, Numpy, Sqlalchemy.

For more information, read the [`Documentation on Python data typess`](https://docs.python.org/3.6/library/stdtypes.html#numeric-types-int-float-complex). 

## Jupyter Notebook Review

> We'll kick our analysis off by checking on three tools: Jupyter Notebook, VS Code, and GitHub.

The first tool we'll check on is Jupyter Notebook. As you already know, Jupyter notebook files are great for sharing code. Since Jupyter Notebook is run in a browser, you will be able to easily share your analysis with W. Avy. All investors will need to do is download the file and run the code you provide.

Check that you have Jupyter Notebook installed by viewing your Applications folder. Open Terminal (on Mac) or Command Prompt (on Windows) and run the command `jupyter --version`. If a version number is returned (any version number is fine) you're good to go. If a version number is not returned, you'll need to reinstall the program.

## VS Code

We'll also be using VS Code in this module to create our Flask application. To make sure you have it installed, go to the Anaconda Navigator application and check the list of applications within the Navigator. If you do not see it in the list, go ahead and install it.

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/N.1.PNG?raw=true)

## Open Starter Jupyter Notebook

Previously, we've opened Jupyter notebook files via the command line. In this module, we'll use a different method: Anaconda Navigator. There is no right or wrong way to open the file; this is just another option at your disposal.

The Jupyter Notebook file, `Your_File.ipynb`, is already downloaded in the surfs_up folder. Navigate to this folder.

Next, open the Anaconda Navigator application, which you should find in the Applications folder. Once you've opened Anaconda-Navigator, find the Jupyter Notebook application icon and click it. This icon should be the top center item, as shown below:

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/N.2.PNG?raw=true)


When you click the Anaconda Navigator icon, a new command line window will open, followed by a webpage showing the files on your computer. Navigate through this file structure to find the surfs_up folder where you saved your `Your_File.ipynb` file. Click the Jupyter Notebook file to open it.

Nice work! Now we're ready to explore SQLite.

## SQLite Advantages
While there are a few specific use cases for SQLite, we'll be focusing on how it can be beneficial to you and where you might get the most value from it. The main advantages are:

1. **It's local.** One of the core advantages of SQLite is that it allows you to create databases locally on your computer to support testing and easy prototyping. This is beneficial, because if you want to test something out and you need a database, it's not always the most convenient to set up a SQL database server just to try something out.
2. **There's an app for that.** Another advantage of SQLite databases are that they can be used on a mobile phone app. Most mobile phone games will use an SQLite database to store certain information about you or your players statistics. While we won't be creating a mobile app in this module, it's still helpful to understand the full context.

## SQLite Disadvantages
SQLite also has a couple of disadvantages, however. They are:

1. **It's local.** If you've used a MYSQL database before, you might have noticed that you can have multiple users access the database. With SQLite, there are no users. SQL is local: stored on one computer or phone. So, only that computer or phone will have access.
2. **There are fewer security features:** one other disadvantage to be aware of is that SQLite doesn't have as many security features as a traditional SQL database. While it's not something specifically to be concerned with for this module, just keep that in mind as you create other databases later on.

Good work with SQLite! Now let's move on to SQLAlchemy.

## SQLAlchemy ORM
One of the primary features of SQLAlchemy is the **Object Relational Mapper**, which is commonly referred to as ORM. ORM allows you to create classes in your code that can be mapped to specific tables in a given database. This allows us to create a special type of system called a **decoupled system**.

To understand ORMs and decoupled systems, consider the following scenario. Suppose you are cleaning out the garage, and you find a bunch of wires or ropes that are all knotted together. We would call this a **tightly coupled system:** all of the different ropes are connected to each other, so if we go to grab just one, the whole mess comes along with it. What the ORM does for us is untangle—or decouple—all of those ropes, so we can use just one of them at a time. When we pick one up, we won't pick up the whole knot; or, if one element breaks, it doesn't affect any of the other cords.

Generally speaking, the less coupling in our code, the better. If there are a bunch of relationships between all of your coding components and one of them breaks, everything breaks.

The ORM helps us keep our systems decoupled. We'll get into more specific details about how we can keep our code decoupled, but for now, just remember that your references will be to classes in your code instead of specific tables in the database, and that we'll be able to influence each class independently.

## SQLAlchemy Create Engine
Another really great feature of SQLAlchemy is the `create engine` function. This function's primary purpose is to set up the ability to query a SQLite database. After all, data just sitting in a database that we can't access does us no good.

In order to connect to our SQLite database, we need to use the `create_engine()` function. This function doesn't actually connect to our database; it just prepares the database file to be connected to later on.

This function will typically have one parameter, which is the location of the SQLite database file. Try this function by adding the following line to your code.

````Python
engine = create_engine("sqlite:///hawaii.sqlite")
````

We've got our engine created—good work! Next we're going to reflect our existing database into a new model with the `automap_base()` function. Reflecting a database into a new model essentially means to transfer the contents of the database into a different structure of data. 

## SQLAlchemy Automap Base
**Automap Base** creates a base class for an automap schema in SQLAlchemy. Basically, it sets up a foundation for us to build on in SQLAlchemy, and by adding it to our code, it will help the rest of our code to function properly.

In order for your code to function properly, you will need to add this line to your code:


````Python
Base = automap_base()
````

Now, after having our refresher on GCS, let's move to our Project!



## Deliverable 1:  Retrieve Weather Data
Generate a set of 2,000 random latitudes and longitudes, retrieve the nearest city, and perform an API call with the OpenWeatherMap. In addition to the city weather data you gathered in this module, use your API skills to retrieve the current weather description for each city. Then, create a new DataFrame containing the updated weather data.

### Deliverable Requirements:

1. Retrieve all of the following information from the API call:
    1. Latitude and longitude
    2. Maximum temperature
    3. Percent humidity
    4. Percent cloudiness
    5. Wind speed
    6. Weather description (for example, clouds, fog, light rain, clear sky)


2. Add the weather data to a new DataFrame
3. Export the DataFrame as WeatherPy_Database.csv into the Weather_Database folder

 
### Results with detail analysis:

1. **Retrieve all of the following information from the API call.**
    1. Latitude and longitude.
    2. Maximum temperature.
    3. Percent humidity.
    4. Percent cloudiness.
    5. Wind speed.
    6. Weather description (for example, clouds, fog, light rain, clear sky).

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# Create an empty list to hold the weather data.
city_data = []
# Print the beginning of the logging.
print("Beginning Data Retrieval     ")
print("-----------------------------")

# Create counters.
record_count = 1
set_count = 1

# Loop through all the cities in the list.
for i, city in enumerate(cities):

    # Group cities in sets of 50 for logging purposes.
    if (i % 50 == 0 and i >= 50):
        set_count += 1
        record_count = 1

    # Create endpoint URL with each city.
    city_url = url + "&q=" + city.replace(" ","+")

    
    # Log the URL, record, and set numbers and the city.
    print(f"Processing Record {record_count} of Set {set_count} | {city}")
    
    # Add 1 to the record count.
    record_count += 1

    # Run an API request for each of the cities.
    try:
    
        # Parse the JSON and retrieve data.
        city_weather = requests.get(city_url).json()
        
        # Parse out the needed data.
        city_lat = city_weather["coord"]["lat"]
        city_lng = city_weather["coord"]["lon"]
        city_max_temp = city_weather["main"]["temp_max"]
        city_humidity = city_weather["main"]["humidity"]
        city_clouds = city_weather["clouds"]["all"]
        city_wind = city_weather["wind"]["speed"]
        city_country = city_weather["sys"]["country"]
        city_description = city_weather["weather"][0]["description"]
        
        # Convert the date to ISO standard.
        city_date = datetime.utcfromtimestamp(city_weather["dt"]).strftime('%Y-%m-%d %H:%M:%S')
        
        # Append the city information into city_data list.
        city_data.append({"City": city.title(),
                          "Lat": city_lat,
                          "Lng": city_lng,
                          "Max Temp": city_max_temp,
                          "Humidity": city_humidity,
                          "Cloudiness": city_clouds,
                          "Wind Speed": city_wind,
                          "Country": city_country,
                          "Current Description": city_description,
                          "Date": city_date})

    # If an error is experienced, skip the city.
    except:
        print("City not found. Skipping...")
        pass


# Indicate that Data Loading is complete.
print("-----------------------------")
print("Data Retrieval Complete      ")
print("-----------------------------") 
````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/1.1.PNG?raw=true)




**2. Add the weather data to a new DataFrame.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# New DF
city_data_df = pd.DataFrame(city_data)
city_data_df.head(10)

# Reorder the column order
new_column_order = ["City", "Country", "Lat","Lng", "Max Temp", "Humidity", "Cloudiness", "Wind Speed", "Current Description", "Date"]

city_data_df = city_data_df[new_column_order]

city_data_df
````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/1.2.PNG?raw=true)


**3. Export the DataFrame as `WeatherPy_Database.csv` into the Weather_Database folder**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# Create the output file (CSV).
output_data_file = "Weather_Database/WeatherPy_Database.csv"
# Export the City_Data into a CSV.
city_data_df.to_csv(output_data_file, index_label="City_ID")
````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/1.3.PNG?raw=true)


![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/1.4.PNG?raw=true)



### Deliverable 2: Create a Customer Travel Destinations Map.
Use input statements to retrieve customer weather preferences, then use those preferences to identify potential travel destinations and nearby hotels. Then, show those destinations on a marker layer map with pop-up markers.

### Deliverable Requirements:

1. Input statements are written to prompt the customer for their minimum and maximum temperature preferences.
2. A new DataFrame is created based on the minimum and maximum temperature, and empty rows are dropped.
3. The hotel name is retrieved and added to the DataFrame, and the rows that don’t have a hotel name are dropped.
4. The DataFrame is exported as a CSV file into the Vacation_Search folder and is saved as `WeatherPy_vacation.csv`.
5. A marker layer map with pop-up markers for the cities in the vacation DataFrame is created, and it is uploaded as a PNG. Each marker has the following information:
    1. Hotel name
    2. City
    3. Country
    4. Current weather description with the maximum temperature
6. The marker layer map is saved and uploaded to the Vacation_Search folder as `WeatherPy_vacation_map.png`.

### Results with detail analysis:

**1. Input statements are written to prompt the customer for their minimum and maximum temperature preferences.**

> Image with `Jupyter Notebook` & `Python` Code below.


**Code and Image**


````Python
# 3. Filter the city_data_df DataFrame using the input statements to create a new DataFrame using the loc method.

# Ask the customer to add a minimum and maximum temperature value.
min_temp = float(input("What is the minimum temperature you would like for your trip? "))
max_temp = float(input("What is the maximum temperature you would like for your trip? "))


````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/2.1.PNG?raw=true)



**2. A new DataFrame is created based on the minimum and maximum temperature, and empty rows are dropped."**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# Filter the dataset to find the cities that fit the criteria.
preferred_cities_df = city_data_df.loc[(city_data_df["Max Temp"] <= max_temp) & \
                                       (city_data_df["Max Temp"] >= min_temp)]
preferred_cities_df.head(10)
````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/2.2.PNG?raw=true)



**3. The hotel name is retrieved and added to the DataFrame, and the rows that don’t have a hotel name are dropped.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# 4a. Determine if there are any empty rows.
preferred_cities_df.notnull().sum()

preferred_cities_df.count()

preferred_cities_df.isnull().sum()

# 4b. Drop any empty rows and create a new DataFrame that doesn’t have empty rows.
preferred_cities_df.dropna()

````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/2.3.PNG?raw=true)

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/2.3a.PNG?raw=true)



**4. The DataFrame is exported as a CSV file into the Vacation_Search folder and is saved as `WeatherPy_vacation.csv`.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# 8a. Create the output File (CSV)
# Create the output file (CSV).
output_data_file = "Vacation_Search/WeatherPy_vacation.csv"

# 8b. Export the City_Data into a csv
hotel_df.to_csv(output_data_file, index_label="City_ID")

````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/2.4.PNG?raw=true)



5. **A marker layer map with pop-up markers for the cities in the vacation DataFrame is created, and it is uploaded as a PNG. Each marker has the following information:**
    1. Hotel name
    2. City
    3. Country
    4. Current weather description with the maximum temperature

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# 9. Using the template add city name, the country code, the weather description and maximum temperature for the city.
info_box_template = """
<dl>
<dt>Hotel Name</dt><dd>{Hotel Name}</dd>
<dt>City</dt><dd>{City}</dd>
<dt>Country</dt><dd>{Country}</dd>
<dt>Current Description</dt><dd>{Current Description}</dd>
<dt>Max Temp</dt><dd>{Max Temp} °F</dd>
</dl>
"""

# 10a. Get the data from each row and add it to the formatting template and store the data in a list.
hotel_info = [info_box_template.format(**row) for index, row in hotel_df.iterrows()]

# 10b. Get the latitude and longitude from each row and store in a new DataFrame.
locations = hotel_df[["Lat", "Lng"]]

# 11a. Add a marker layer for each city to the map. 
max_temp = hotel_df["Max Temp"]
fig = gmaps.figure(center=(30.0, 31.0), zoom_level=1.5)
heat_layer = gmaps.heatmap_layer(locations, weights=max_temp,dissipating=False,
             max_intensity=300, point_radius=4)
marker_layer = gmaps.marker_layer(locations, info_box_content=hotel_info)
fig.add_layer(heat_layer)
fig.add_layer(marker_layer)

# 11b. Display the figure
fig

````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/2.5.PNG?raw=true)


**6. The marker layer map is saved and uploaded to the Vacation_Search folder as `WeatherPy_vacation_map.png`.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/2.6.PNG?raw=true)




## Deliverable 3: Create a Travel Itinerary Map
Use the Google Directions API to create a travel itinerary that shows the route between four cities chosen from the customer’s possible travel destinations. Then, create a marker layer map with a pop-up marker for each city on the itinerary.

### Deliverable Requirements:

1. Four DataFrames are created, one for each city on the itinerary. 
2. The latitude and longitude pairs for each of the four cities are retrieved. 
3. A directions layer map between the cities and the travel map is created and uploaded as `WeatherPy_travel_map.png`. 
4. A DataFrame that contains the four cities on the itinerary is created.
5. A marker layer map with a pop-up marker for the cities on the itinerary is created, and it is uploaded as `WeatherPy_travel_map_markers.png`. Each marker has the following information: 
    1. Hotel name
    2. City
    3. Country
    4. Current weather description with the maximum temperature


### The analysis should contain the following:

1. **Four DataFrames are created, one for each city on the itinerary** 
Explain the purpose of the new analysis:

**Code and Image**


````Python
# Start Vacation at:

vacation_start = mexico_vacation_df.loc[(mexico_vacation_df["City_ID"] == stop1)]
vacation_start = vacation_start.iloc[0]

vacation_stop1 = mexico_vacation_df.loc[(mexico_vacation_df["City_ID"] == stop2)]
vacation_stop1 = vacation_stop1.iloc[0]

vacation_stop2 = mexico_vacation_df.loc[(mexico_vacation_df["City_ID"] == stop3)]
vacation_stop2 = vacation_stop2.iloc[0]

vacation_stop3 = mexico_vacation_df.loc[(mexico_vacation_df["City_ID"] == end)]
vacation_stop3 = vacation_stop3.iloc[0]

vacation_end = mexico_vacation_df.loc[(mexico_vacation_df["City_ID"] <= end)]
vacation_end = vacation_end.iloc[0] 
````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/3.1.PNG?raw=true)


2. **The latitude and longitude pairs for each of the four cities are retrieved.** 
Using images from the summary DataFrame and multiple-line chart, describe the differences in ride-sharing data among the different city types:
  
**Code and Image**


````Python
start = vacation_start[["Lat", "Lng"]]
stop1 = vacation_stop1[["Lat", "Lng"]]
stop2 = vacation_stop2[["Lat", "Lng"]]
stop3 = vacation_stop3[["Lat", "Lng"]]
end = vacation_end[["Lat", "Lng"]]
````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/3.2.PNG?raw=true)
   

3. **A directions layer map between the cities and the travel map is created and uploaded as `WeatherPy_travel_map.png`.** 
types:
  
**Code and Image**


````Python
# 7. Create a direction layer map using the start and end latitude-longitude pairs,
# and stop1, stop2, and stop3 as the waypoints. The travel_mode should be "DRIVING", "BICYCLING", or "WALKING".

# USING DRIVING MODE!

import gmaps
import gmaps.datasets
gmaps.configure(api_key=g_key)

start = (20.7, -105.2)
stop1 = (17.48, -91.43)
stop2 = (27.98, -114.06)
stop3 = (23.17, -97.95)
end = (30.85, -116.07)

fig = gmaps.figure()
sart2end_via_stops = gmaps.directions_layer(
        start, end, waypoints=[stop1, stop2, stop3],
        travel_mode='DRIVING')
fig.add_layer(sart2end_via_stops)
fig

````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Vacation_Itinerary/WeatherPy_travel_map.PNG?raw=true)
    

 4. **A DataFrame that contains the `four` cities on the itinerary is created.** 
types:
  
**Code and Image**


````Python
# 8. To create a marker layer map between the cities.
#  Combine the four city DataFrames into one DataFrame using the concat() function.

mexico_vacation_df = pd.concat([mexico_vacation_df],ignore_index=True)
mexico_vacation_df

# 9 Using the template add city name, the country code, the weather description and maximum temperature for the city. 
info_box_template = """
<dl>
<dt>City</dt><dd>{City}</dd>
<dt>Country</dt><dd>{Country}</dd>
<dt>Current Description</dt><dd>{Current Description}</dd>
<dt>Max Temp</dt><dd>{Max Temp} °F</dd>
</dl>
"""

# 10a Get the data from each row and add it to the formatting template and store the data in a list.
mark_info = [info_box_template.format(**row) for index, row in mexico_vacation_df.iterrows()]

# 10b. Get the latitude and longitude from each row and store in a new DataFrame.
locations = mexico_vacation_df[["Lat", "Lng"]]
````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Resources/Images/3.4.PNG?raw=true)
    
 5. **A marker layer map with a pop-up marker for the cities on the itinerary is created, and it is uploaded as `WeatherPy_travel_map_markers.png`. Each marker has the following information:**

    1. Hotel name
    2. City
    3. Country
    4. Current weather description with the maximum temperature

> Image with `Jupyter Notebook` & `Python` Code below.

````Python
# 11a. Add a marker layer for each city to the map.
city_mark = mexico_vacation_df["City"]
fig = gmaps.figure(center=(30.0, 31.0), zoom_level=1.5)
marker_layer = gmaps.marker_layer(locations, info_box_content=mark_info)

fig.add_layer(marker_layer)
fig
````

![name-of-you-image](https://github.com/emmanuelmartinezs/World_Weather_Analysis/blob/main/Vacation_Itinerary/WeatherPy_travel_map_markers.PNG?raw=true)


#### Surf Up Analysis Completed by Emmanuel Martinez
