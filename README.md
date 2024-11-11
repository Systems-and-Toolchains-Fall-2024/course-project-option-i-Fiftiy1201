[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/VuODydzp)

<details>
<summary>Click to see feature descriptions</summary>
- **sofifa_ID**: unique player ID on sofifa  
- **player_url**: URL of the scraped player  
- **short_name**: player short name  
- **long_name**: player long name  
</details>

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
- dob: playet data of birth
- height_cm: player height (in cm)
- weight_kg: player weight (in kg)
- club_team_id: club team_id on sofifa where the player plays
- league_name: league name of the club
- league_level: league rank of the club (e.g. English Premier League is 1, English League Championship is 2, etc.)
- club_position: player position in the club (e.g. SUB means substitute, RES means reserve)
- club_jersey_number: player jersey number in the club
- club_loaned_from: club loaning out the player - if applicable
- club_joined: date when the player joined his current club
- club_contract_valid_until
- nationality_id: player nationality id on sofifa
- nationality_name: player nationality name
- nation_team_id: national team_id on sofifa where the player plays
- nation_position: player position in the national team
- nation_jersey_number: player jersey number in the national team
- preferred_foot: player preferred foot
- weak_foot: player weak foot attribute
- skill_moves: player skill moves attribute
- international_reputation: player international reputation attribute
- work_rate: player work rate attributes (attacking / defensive)
- body_type: player body type
- real_face: player real face
- release_clause_eur: player release clause (in EUR) - if applicable
- player_tags: player tags
- player_traits: player traits
- pace: player pace attribute
- shooting: player shooting attribute
- passing: player passing attribute
- dribbling: player dribbling attribute
- defending: player defending attribute
- physic: player physic attribute
- attacking_crossing: player crossing attribute
- attacking_finishing: player finishing attribute
- attacking_heading_accuracy: player heading accuracy attribute
- attacking_short_passing: player short passing attribute
- attacking_volleys: player volleys attribute
- skill_dribbling: player dribbling attribute
- skill_curve: player curve attribute
- skill_fk_accuracy: player free-kick accuracy attribute
- skill_long_passing: player long passing attribute
- skill_ball_control: player ball control attribute
- movement_acceleration: player acceleration attribute
- movement_sprint_speed: player sprint speed attribute
- movement_agility: player agility attribute
- movement_reactions: player reactions attribute
- movement_balance: player balance attribute
- power_shot_power: player shot power attribute
- power_jumping: player jumping attribute
- power_stamina: player stamina attribute
- power_strength: player strength attribute
- power_long_shots: player long shots attribute
- mentality_aggression: player aggression attribute
- mentality_interceptions: player interceptions attribute
- mentality_positioning: player positioning attribute
- mentality_vision: player vision attribute
- mentality_penalties: player penalties attribute
- mentality_composure: player composure attribute
- defending_marking_awareness: player marking awareness attribute
- defending_standing_tackle: player standing tackle attribute
- defending_sliding_tackle: player sliding tackle attribute
- goalkeeping_diving: player GK diving attribute
- goalkeeping_handling: player GK handling attribute
- goalkeeping_kicking: player GK kicking attribute
- goalkeeping_positioning: player GK positioning attribute
- goalkeeping_reflexes: player GK reflexes attribute
- goalkeeping_speed: player GK speed attribute
- ls: player attribute playing as LS
- st: player attribute playing as ST
- rs: player attribute playing as RS
- lw: player attribute playing as LW
- lf: player attribute playing as LF
- cf: player attribute playing as CF
- rf: player attribute playing as RF
- rw: player attribute playing as RW
- lam: player attribute playing as LAM
- cam: player attribute playing as CAM
- ram: player attribute playing as RAM
- lm: player attribute playing as LM
- lcm: player attribute playing as LCM
- cm: player attribute playing as CM
- rcm: player attribute playing as RCM
- rm: player attribute playing as RM
- lwb: player attribute playing as LWB
- ldm: player attribute playing as LDM
- cdm: player attribute playing as CDM
- rdm: player attribute playing as RDM
- rwb: player attribute playing as RWB
- lb: player attribute playing as LB
- lcb: player attribute playing as LCB
- cb: player attribute playing as CB
- rcb: player attribute playing as RCB
- rb: player attribute playing as RB
- gk: player attribute playing as GK
- player_face_url: URL of the player face
- club_logo_url: URL of the club logo
- club_flag_url: URL of the club nationality flag
- nation_logo_url: URL of the national team logo
- nation_flag_url: URL of the national flag


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
