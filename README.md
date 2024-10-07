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

### Using PostgreSQL DB table over NoSQL DB
Our dataset is in tabular, structured format. PostgreSQL is a relational database with defined columns and data types. Using PostgreSQL is beneficial because we want to maintain the tabular structure of our data. In contrast, NoSQL databases are generally suitable for unstructured or semi-structured data, because NoSQL has no schema and often uses aggreagates which increases flexibility.

Also, our dataset is not too large and is able to be run on a single computer. We don't need the scalable advantage of NoSQL. We would prefer to have PostgreSQL's ACID (Atomicity, Consistency, Isolation, Durability) support than NoSQL's concept of favoring performance over full consistency.
