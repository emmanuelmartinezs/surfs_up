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

Now, after having our refresher, let's move to our Project!



## Deliverable 1:  Determine the Summary Statistics for June
Using Python, Pandas functions and methods, and SQLAlchemy, you’ll filter the date column of the Measurements table in the `hawaii.sqlite` database to retrieve all the temperatures for the month of June. You’ll then convert those temperatures to a list, create a DataFrame from the list, and generate the summary statistics.

### Deliverable Requirements:
You will earn a perfect score for Deliverable 1 by completing all requirements below:

1. A working query is written to retrieve the June temperatures from the `date` column of the `Measurement` table.
2. The temperatures are added to a list.
3. ​The list of temperatures is converted to a Pandas DataFrame.
4. Summary statistics are generated for the DataFrame.

 
### Results with detail analysis:

1. **A working query is written to retrieve the June temperatures from the `date` column of the `Measurement` table.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# By Emmanuel Martinez
# Module 9

%matplotlib inline
from matplotlib import style
style.use('fivethirtyeight')
import matplotlib.pyplot as plt

# Dependencies
import numpy as np
import datetime as dt
import pandas as pd

# Python SQL toolkit and Object Relational Mapper
import sqlalchemy
from sqlalchemy.ext.automap import automap_base
from sqlalchemy.orm import Session
from sqlalchemy import create_engine, func

engine = create_engine("sqlite:///hawaii.sqlite")

# reflect an existing database into a new model
Base = automap_base()
# reflect the tables
Base.prepare(engine, reflect=True)

# Save references to each table
Measurement = Base.classes.measurement
Station = Base.classes.station

# Create our session (link) from Python to the DB
session = Session(engine)

engine = create_engine("sqlite:///hawaii.sqlite")

# reflect an existing database into a new model
Base = automap_base()
# reflect the tables
Base.prepare(engine, reflect=True)

# Save references to each table
Base.classes.keys()

# We can view all of the classes that automap found
Measurement = Base.classes.measurement
Station = Base.classes.station

# Create our session (link) from Python to the DB
session = Session(engine)

# 1. Import the sqlalchemy extract function.
from sqlalchemy import extract

# 2. Write a query that filters the Measurement table to retrieve the temperatures for the month of June. 
session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date)==6).all()
````

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/1.1.PNG?raw=true)


2. **The temperatures are added to a list.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
#  3. Convert the June temperatures to a list.
results = session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date)==6).all()
````

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/1.2.PNG?raw=true)


3. **​The list of temperatures is converted to a Pandas DataFrame.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# 4. Create a DataFrame from the list of temperatures for the month of June. 
df = pd.DataFrame(results, columns=['date','temperature'])
df.set_index(df['date'], inplace=True)
````

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/1.3.PNG?raw=true)


4. **​Summary statistics are generated for the DataFrame.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# 5. Calculate and print out the summary statistics for the June temperature DataFrame.
df.describe()
````

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/1.4.PNG?raw=true)


### Deliverable 2: Determine the Summary Statistics for December.
Using Python, Pandas functions and methods, and SQLAlchemy, you’ll filter the date column of the Measurements table in the `hawaii.sqlite` database to retrieve all the temperatures for the month of December. You’ll then convert those temperatures to a list, create a DataFrame from the list, and generate the summary statistics.

### Deliverable Requirements:
You will earn a perfect score for Deliverable 2 by completing all requirements below:

1. A working query is written to retrieve the December temperatures from the `date` column of the `Measurement` table.
2. The temperatures are added to a list.
3. ​The list of temperatures is converted to a Pandas DataFrame.
4. Summary statistics are generated for the DataFrame

### Results with detail analysis:

1. **A working query is written to retrieve the December temperatures from the `date` column of the `Measurement` table.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# 6. Write a query that filters the Measurement table to retrieve the temperatures for the month of December.
session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date)==12).all()
````

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/2.1.PNG?raw=true)


2. **The temperatures are added to a list.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# 7. Convert the December temperatures to a list.
results = session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date)==12).all()
````

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/2.2.PNG?raw=true)


3. **​The list of temperatures is converted to a Pandas DataFrame.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# 8. Create a DataFrame from the list of temperatures for the month of December. 
df = pd.DataFrame(results, columns=['date','temperature'])
df.set_index(df['date'], inplace=True)
````

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/2.3.PNG?raw=true)


4. **​Summary statistics are generated for the DataFrame.**

> Image with `Jupyter Notebook` & `Python` Code below.

**Code and Image**


````Python
# 9. Calculate and print out the summary statistics for the Decemeber temperature DataFrame.
df.describe()
````

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/2.4.PNG?raw=true)



## Deliverable 3: A written report for the statistical analysis
For this part of the Challenge, write a report that describes the key differences in weather between June and December and two recommendations for further analysis.

### The analysis should contain the following:

1. **Overview of the analysis:** Using Python, Pandas functions and methods, and SQLAlchemy, we’ll filter the date column of the Measurements table in the `hawaii.sqlite` database to retrieve all the temperatures for the month of June. We'll then convert those temperatures to a list, create a DataFrame from the list, and generate the summary statistics. Once our dataframe is created we are able to get our summary statistics by using the `df.describe()` code and method. 
> Below our Analysis that what we found:

2. **Results:** Data Provided gave us a visibility that on months of June and December, our location had a total Temps of:

**June Temps - Analysis and Result**
* Count of 1700 
* Mean of 74.94 
* Std of 3.26 
* Min of 64.00 
* 25% of 73.00 
* 50% of 75.00
* 75% of 77.00
* Max of 85.00


**June Temps - Report**
> Image with `Jupyter Notebook` & `Python` Code below.

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/1.4.PNG?raw=true)



**December Temps - Analysis and Result**
* Count of 1517 
* Mean of 71.04 
* Std of 3.75
* Min of 56.00 
* 25% of 69.00 
* 50% of 71.00
* 75% of 74.00
* Max of 83.00


**December Temps - Report**
> Image with `Jupyter Notebook` & `Python` Code below.

![name-of-you-image](https://github.com/emmanuelmartinezs/surfs_up/blob/main/Resources/Images/2.4.PNG?raw=true)


3. **Summary:** Based on our Data Analysis, Data Provided, we can state as a high-level summary of results that Standard deviation is 3.25 in June and 3.75 in December, making a 0.5 difference between both seasons.
 
    In addition, current data provide attributes such precipitation and others, with two queries that our analysis pursue, performing weather data for June and December that helps results to decide how we would like to build the shop and what areas would make this location attractive to visitors to stop by and have a successful business.

#### Surf Up Analysis Completed by Emmanuel Martinez
