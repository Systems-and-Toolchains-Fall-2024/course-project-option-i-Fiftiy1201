[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/VuODydzp)


## Group: Lixin Xu, Helen Yu

# Feature descriptions

<details>
<summary>Feature Descriptions</summary>

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
- gender: player gender
- year: year data collected

</details>

# Installation and Steps to run the code
1. Follow typical methods to configure your PostgreSQL database and install pyspark in your virtual environment
2. Download all data files ending in ```.csv``` from this github repo's ```data/``` folder to the ```data/``` folder in your local working directory. Do NOT change the name of the data file. Your working directory should look like this:
    - folder: ```data```
        - players_15.csv
        - ....
    - file: ```project.ipynb```
3. Change the ```username```, ```password```, ```url``` in ```db_properties``` (section highlighed) to those specific to your PostgreSQL database's 
4. Start your postgresSQL service and run the ```project.ipynb``` code file from the beginning sequentially.

### Instructions on using the Feature Engineering part of the code
This part has two modes:
    - ***MODE 1 - `proceed=FALSE`***: this mode is for users to know the necessary information for preprocessing, cleaning, and feature-engineering the dataset. It will print out number of nulls, number of outliers, and correlation matrix of the columns, but will not change anything about the data.
    - ***MODE 2 - `proceed=TRUE`***: this mode will execute the specified edits to the dataframe and print out necessay before- and after-edit data to ensure the edit is successful.
***Steps:***
1. Run MODE 1 first, then from results, decide:
   - Which columns to drop, if so, set `drop=True` when instantiating MissingValueHandler(), then specify the the column names in the class definition.
   - Which columns to impute, if so, set `impute_num=True` or `impute_cat=True` when instantiating MissingValueHandler(), then speficy the names of the columns in `num_impute_list` in the class definition.
   - Threshold for number of outliers to drop,  set `drop=True` and `num_outlier_thres=<that threshold>` when instantiating MissingValueHandler()
   - Which correlated columns to drop, set `drop=True` when instantiating CorrelationHandler(), specify the name of the columns in `correlated_cols` in the class definition.
   - If any column needs to be log transformed, specify its name in `LogTransformer` class definition.
3. Run MODE 2 witht the parameter settings described above.

## Function Inputs
### Function 1
- ```df``` your original pyspark dataframe containing only data of male players
- ```X``` is a year between (2015 and 2022, inclusively), in ```str```
- ```Y``` is the number of clubs returned, a positive integer, in ```int```.
- ```Z``` is a year that can hold the value of 2023 or a year after it, in ```str```
- 
### Function 2
- ```df``` your original pyspark dataframe containing only data of male players
- ```X``` represents the number of clubs returned, a positive integer, in ```int```
- ```Y``` represents a year between 2015 and 2022 inclusively, in ```str```
- ```orderby``` could either be 'highest' or 'lowest' in ```str```, which respectively mean the use wants the highest average age or the lowest average age.
- 
### Function 3
- ```df``` your original pyspark dataframe containing only data of male players

### calculate_r2(y_true, y_pred), return r2
- #### Parameters: 
- ```y_true```: The true target values, provided as a tensor.
- ```y_pred```: The predicted values from the model, provided as a tensor.
- #### Returns:
- ```r2```: A floating-point value representing the R² score, which indicates how well the predictions approximate the true values, with 1 being a perfect fit.
- 
### def train_model(model, train_loader, test_loader, learning_rate, num_epochs):, return avg_loss, train_losses, model 
- #### Parameters:
- ```model```: The PyTorch model to be trained.
- ```train_loader```: A PyTorch DataLoader object for loading the training data in batches.
- ```test_loader```: A PyTorch DataLoader object for loading the test data in batches.
- ```learning_rate```: A floating-point value specifying the learning rate for the optimizer.
- ```num_epochs```: An integer specifying the number of training epochs.
- #### Returns:
- ```avg_loss```: The average loss over the entire training dataset.
- ```train_losses```: A list of loss values recorded at each epoch, which can be used for plotting the training loss curve.
- ```model```: The trained PyTorch model after completing the specified number of epochs.

# Explanation on methods

## Using PostgreSQL DB table over NoSQL DB
Our dataset is in tabular, structured format. PostgreSQL is a relational database with defined columns and data types. Using PostgreSQL is beneficial because we want to maintain the tabular structure of our data. In contrast, NoSQL databases are generally suitable for unstructured or semi-structured data, because NoSQL has no schema and often uses aggreagates which increases flexibility.

Also, our dataset is not too large and is able to be run on a single computer. We don't need the scalable advantage of NoSQL. We would prefer to have PostgreSQL's ACID (Atomicity, Consistency, Isolation, Durability) support than NoSQL's concept of favoring performance over full consistency.

## PySpark
For PySpark, the two selected regressors were Random Forests Regressor and Linear Regressor. The Random forest regressor was selected because it handles string-index categorical data well, where categories are represented numerically but the magnitude of the numbers do not imply real-life meanings. The Linear Regressor was chosen for its efficiency and straightforward implementation in handling linearly related data, which makes it a good baseline model in comparison with more complex methods.

Tunable parameters for random forests:
- Number of Trees (numTrees): Increasing the number of trees generally improved model stability and accuracy, though the improvement in accuracy brought by increasing number of treess becomes smaller at high values of numTrees.
- Max Depth (maxDepth): Controls the depth of each tree, balancing model complexity and overfitting. Shallow trees had faster training times but lower accuracy, while deeper trees had improved accuracy with the risk of overfitting.

Tunable Parameters for Linear Regression:
- Regularization Parameter (regParam): This parameter controls the degree of regularization applied to the Linear Regressor, which helps reduce overfitting by penalizing large weights. Lower values of regParam allow the model to fit the data more closely, which can be beneficial in cases with simpler data but may lead to overfitting on more complex datasets. Higher values provide stronger regularization, which can improve generalization but may cause underfitting.
- maxIter: This parameter determines the maximum number of iterations for the optimization algorithm. Increasing maxIter can allow the model more time to converge to the optimal solution, which may improve accuracy, especially if the dataset is large or complex. However, very high values for maxIter may lead to longer training times without significant accuracy gains.

The Random Forest and Linear Regression models were chosen for their complementary strengths: Random Forests provide better handling of complex feature interactions and categorical data, while Linear Regression serves as an effective, interpretable baseline. By comparing both models, it’s possible to assess the linear versus non-linear relationships within the data and gain insights into model performance on this dataset.

## PyTorch
For PyTorch, two models were selected, a deep NN and a shallow NN. For the shallow NN, it was constructed with only one hidden layer of 64 neurons. The deep NN, has a more complex structure, with 4 hidden layers containing 128, 64, 32, and 16 neurons respectively. 

Tunable parameters for neural networks: 

- Learning Rate: Controls how big are the steps that the model takes to update weights. Higher learning rates can speed up convergence and help avoid stucking in local minima, but may risk overshooting and unstable training. Lower learning rates offer stability but may increase the time needed for convergence and may get model stuck in local minima. During tuning, we observed that lower learning rates (e.g., 0.0005) led to better performance in both deep and shallow NN, and we didn't see a visually obvious difference between them.

- Epochs: The number of complete passes through the training dataset. Higher epoch counts typically improve accuracy by allowing the model more opportunities to learn more, though excessive epochs can lead to overfitting. Increasing epochs improved the accuracy of both shallow and deep NN model up to a certain threshold, after which led to overfitting. The DeepNN, in particular, we saw it significantly benefited from higher epochs (we compared 10 vs 40), as it has large amount of parameters and need more training iterations to learn.

If needed, we could also adjust the number of hidden layers and number of neurons in each hidden layer to increase model accuracy. To compare the shallow and deep NN, with more hidden layers, the deep NN therotically should achieve lower losses and higher accuracy on test data, because it's able to capture more complex features than shallow NN. But this also requires more time to train the data compared to shallow NN. While deep NN has the capability to perform better on training and test data, its structure also makes it prone to overfitting problems.
