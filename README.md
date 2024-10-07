[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/VuODydzp)
## Group: Lixin Xu, Helen Yu
## Feature description
- sofifa_ID: unique player ID on sofifa
- player_url: URL of the scraped player
- short_name: player short name
- long_name: player long name
- player_positions: player preferred positions
- overall: player current overall attribute
- potential: player potential overall attribute
- value_eur: player value (in EUR)
- wage_eur: player weekly wage (in EUR)
- age: player age

## Using PostgreSQL DB table over NoSQL DB
Our dataset is in tabular, structured format. PostgreSQL is a relational database with defined columns and data types. Using PostgreSQL is beneficial because we want to maintain the tabular structure of our data. In contrast, NoSQL databases are generally suitable for unstructured or semi-structured data, because NoSQL has no schema and often uses aggreagates which increases flexibility.

Also, our dataset is not too large and is able to be run on a single computer. We don't need the scalable advantage of NoSQL. We would prefer to have PostgreSQL's ACID (Atomicity, Consistency, Isolation, Durability) support than NoSQL's concept of favoring performance over full consistency.

## Installation and Steps to run the code
1. Follow typical methods to configure your PostgreSQL database and install pyspark in your virtual environment
2. Download all data files ending in ```.csv``` from this github repo's ```data/``` folder to the ```data/``` folder in your local working directory. Do NOT change the name of the data file. Your working directory should look like this:
    - folder: ```data```
        - players_15.csv
        - ....
    - file: ```project.ipynb```
3. Change the ```username```, ```password```, ```url``` in ```db_properties``` (section highlighed) to those specific to your PostgreSQL database's 
4. Start your postgresSQL service and run the ```project.ipynb``` code file from the beginning sequentially.

## Function Inputs
### Function 1
- ```df``` your original pyspark dataframe containing only data of male players
- ```X``` is a year between (2015 and 2022, inclusively), in ```str```
- ```Y``` is the number of clubs returned, a positive integer, in ```int```.
- ```Z``` is a year that can hold the value of 2023 or a year after it, in ```str```

### Function 2
- ```df``` your original pyspark dataframe containing only data of male players
- ```X``` represents the number of clubs returned, a positive integer, in ```int```
- ```Y``` represents a year between 2015 and 2022 inclusively, in ```str```
- ```orderby``` could either be 'highest' or 'lowest' in ```str```, which respectively mean the use wants the highest average age or the lowest average age.
### Function 3
- ```df``` your original pyspark dataframe containing only data of male players
