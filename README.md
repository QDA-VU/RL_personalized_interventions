Repo for knowledge transfer between the group members working on RL for personalized interventions.


### REINFORCE study
https://www.nature.com/articles/s41746-024-01028-5

##### Preprocessed dataset
`reinforce_preprocessed_withDemographics.npy` holds the REINFORCE holds the preprocessed timeserie dataset in the form of a numpy tensor shape (N, T, D) where N is the number of patients, T the number of days, D the number of dimensions.

The missing data (`.`) from the unprocessed dataset has been replaced by `0`.

##### Raw dataset 

-  `Factors by day.csv` has action space
  - per patients, per day, 5 features, the reminder has 
    - "5 behavioral factors for the messages: (1) framing (classified as neutral, positive [invoking positive outcomes of medication use], or negative [invoking consequences of medication non-use]), (2) observed feedback (“History”, i.e., including the number of days in the prior week the patient was adherent), (3) social reinforcement (“Social”), (4) whether content was reminder or informational (“Content”), and (5) whether the text included a reflective question (“Reflective”); We designed ≥2 text messages for each unique set of factors (i.e., 47 unique sets across 128 text messages);"
- `Adherence by day.csv` has observation space (rewards)
  - per day, value in $[0,1]$ meaning the fraction of the daily medication taken by a patient
-  `Dataverse main analytic file.csv` has demographic data on patients 
###### data shape (n_participants, n_timepoints, n_dimensions) = (29, 184, 18)
###### data dimensions
1. adherence - value in $[0,1]$ meaning the fraction of the daily medication taken by a patient 

3. framing_sms
4. history_sms
5. social_sms
6. content_sms
7. reflective_sms
8. framing_pos
9. framing_neg

10. age_years
11. number_meds
12. sex_encoded - 0 female, 1 male
13. edu_level_encoded - 0 "Some high school/Below high school", 1 "Some college", 2 "College Grad/Postgrad"
14. marital_status_encoded - 0 Widow/divorced/single/other', 1 Married/partner
15. race_Asian - participant race is one-hot encoded
16. race_Black/African American
17. race_Hispanic/Latinx
18. race_Prefer not to say
19. race_White


### Smoking study
https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0277295

##### Preprocessed dataset
`smoking_data_for_ML.npy` holds the preprocessed timeserie dataset in the form of a numpy tensor shape (N, T, D) where N is the number of patients, T the number of days, D the number of dimensions.

###### data shape: (499, 4, 18)
	- removed 22 participants bc they had missing values

###### data dimensions:

- dim 0 = effort
	- target dimension
	-  (int: 0-10, "Effort" column in df_pers_single_nona.csv )			
	- adherence: the effort the person put into performing the recommended activity 
- dim 1 = persuasive message type
	- control dimension
	-  (int: 0-4, the first 4 values in the cells on the "action_type_index_list" column in the raw dataset `conversational_sessions_anonym.csv` )
  - The text messages corresponding to the indeces are in `list_persuasiveMessages_smoking.pkl`. 

	- "Indices of persuasion types used in sessions 1-5. The persuasion types are commitment (0), consensus (1), authority (2), action planning (3), and no persuasion (4)."
- dim 2 = activity recommended
	- control dimension
	-  (int: 1-24, "Activity" column in `df_pers_single_nona.csv` )		
	- Index of the assigned activity. There are a total of 24 different activities, and the index goes from 1 to 24.
  - The text description of the activities corresponding to the indeces are in `list_activities_smoking.pkl`. 
- dim 3 = type of activity recommended
	- control dimension
	-  (int: 1-2, "PA_Activity" column in the raw dataset `df_pers_single_nona.csv` )		
	- Whether the assigned activity was for smoking cessation (1) or increasing physical activity (2).
- dim 4+ = demographics
	- description in `df_pers_single_nona_data_explanation.csv`
	- TTM_Smoking, TTM_PA, NFC, Pers_Extraversion, Pers_Agreeableness, Pers_Conscientiousness, Pers_ES, Pers_OE, Involvement, age, Gender identity, PA_Identity, Quitting_Self_Identity, Quit_Before_24h
