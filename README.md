# RL_personalized_interventions
Repo for knowledge transfer between the group members working on RL for personalized interventions.


### REINFORCE study

#### Preprocessed dataset
`tensor_Reinforce.npy` holds the REINFORCE timeserie dataset preprocessed in the form of a numpy tensor shape (N, T, D) where N is the number of patients, T the number of days, D holds on dimension 0 the value of adherence, and on dimensions 1-5 the 5 reminder factors. 

The missing data (`*`) from the unprocessed dataset has been replaced by `0`.

#### Raw dataset 

-  `Factors by day.csv` has action space
  - per patients, per day, 5 features, the reminder has 
    - "5 behavioral factors for the messages: (1) framing (classified as neutral, positive [invoking positive outcomes of medication use], or negative [invoking consequences of medication non-use]), (2) observed feedback (“History”, i.e., including the number of days in the prior week the patient was adherent), (3) social reinforcement (“Social”), (4) whether content was reminder or informational (“Content”), and (5) whether the text included a reflective question (“Reflective”); We designed ≥2 text messages for each unique set of factors (i.e., 47 unique sets across 128 text messages);"
- `Adherence by day.csv` has observation space (rewards)
  - per day, value in $[0,1]$ meaning the fraction of the daily medication taken by a patient
-  `Dataverse main analytic file.csv` has demographic data on patients 
