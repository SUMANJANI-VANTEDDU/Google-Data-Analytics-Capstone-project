# GOOGLE DATA ANALYTICS CAPSTONE PROJECT #
## BELLABEAT CASE STUDY ##
(using excel, sql and tableau)

### INTRODUCTION: ###
Bellabeat is a high-tech manufacturer of health-focused products for women. It is a successful small company, but they have potential to become a larger player in the global smart device market.
- Cofounder & cheif creative officer : ***Urška Sršen***
- Mathematician and Bellabeat’s cofounder; key member of the Bellabeat executive team : ***Sando Mur***
- Bellabeat marketing analytics team.

#### PRODUCTS OF BELLABEAT: ####
#### 1.Bellabeat app: ####
provides health data related to their:
   - Activity
   - Sleep
   - Stress
   - Menustral cycle
   - Mindfulness habits

Understands their current habits and make healthy decisions.

Connects to the wellness products.

#### 2.Leaf: ####
Worn as:
- Bracelet
- Necklace
- Clip
  
The Leaf tracker connects to the Bellabeat app to track activity, sleep, and stress.

#### 3.Time: #### 
- This wellness watch combines the timeless look of a classic timepiece with smart technology to track user activity, sleep, and stress.
- The Time watch connects to the Bellabeat app to provide you with insights into your daily wellness.

#### 4.Spring: #### 
- This is a water bottle that tracks daily water intake.
- The Spring bottle connects to the Bellabeat app to track your hydration levels.

#### 5.Bellabeat membership: #### 
- Offers subscription-based membership program for users.
- Membership gives users 24/7 access to fully personalized guidance on nutrition, activity, sleep, health and
beauty, and mindfulness based on their lifestyle and goals.

#### ABOUT THE COMPANY: ####
- Tech-driven wellness company.
- Founded in 2013.
- Collecting data on: activiy, sleep, stress, reproductive health.
- Opened offices and launched multiple products in 2016.
- Invested in advertising: radio, print, billboards, television, digital marketing.
- Digital marketing includes- google search, facebook, instagram, twitter, youtube and ads on google display network.

#### BUSINESS TASK: ####
Focus on one of the bellabeat’s products and analyze smart device data to gain insight into how consumers are using their smart devices.

#### DATA ANALYSIS PROCESS: ####
we use data analysis process to analyze the casestudy and provide our recommendations according to the achieved results.
1. ASK
2. PREPARE
3. PROCESS
4. ANALYZE
5. SHARE
6. ACT

### 1. ASK: ###
1. What are some trends in smart device usage?
2. How could these trends apply to Bellabeat customers?
3. How could these trends help influence Bellabeat marketing strategy?

### 2. PREPARE: ###
Used public dataset from kaggle  
[ https://www.kaggle.com/datasets/arashnic/fitbit ] 
- This dataset consists of personal data related to 30 fitbit users.
- The dataset I used covers the timeperiod from 4/12/2016 to 5/12/2016.
- There are 18 datasets related to this timeperiod.
- stored as "sandbox-first-project.bellabeat"
#### Limitations: ####
- repeated data.
- some of the data is incomplete.
- limited number of users data.

### 3. PROCESS: ###
18 datasets in the fitbit fitness tracker public data:
1. dailyActivity_merged.csv
2. dailyCalories_merged.csv
3. dailyIntensities_merged.csv
4. dailySteps_merged.csv
5. heartrate_seconds_merged.csv
6. hourlyCalories_merged.csv
7. hourlyIntensities_merged.csv
8. hourlySteps_merged.csv
9. minuteCaloriesNarrow_merged.csv
10. minuteCaloriesWide_merged.csv
11. minuteIntensitiesNarrow_merged.csv
12. minuteIntensitiesWide_merged.csv
13. minuteMETsNarrow_merged.csv
14. minuteSleep_merged.csv
15. minuteStepsNarrow_merged.csv
16. minuteStepsWide_merged.csv
17. sleepDay_merged.csv
18. weightLogInfo_merged

The datasets I used:
-    dailyActivity_merged
-    sleepDay_merged
-    weightLogInfo
-    minuteSleep_merged
-    heartrate_seconds_merged
-    minuteMETsNarrow_merged

#### Tools used: ####
- 'Google sheets' for merging, sorting and filtering data.
- 'BigQuery' for querying data in SQL.
- 'Tableau' for data visualization.

### 4.ANALYZE: ###
- checking for distinct values.
```

   select
       'dailyactivity_Ids',count(distinct(Id))
   from
       `sandbox-first-project-1.bellabeat.daily_activity`
   union all
   select
       'heartrate_Ids',count(distinct(Id))
   from
       `sandbox-first-project-1.bellabeat.heartrate_seconds`
   union all
   select
        'sleepday_Ids', count(distinct(Id))
   from 
        `sandbox-first-project-1.bellabeat.sleep_day`
   union all
   select
       'weightlog_Ids',count(distinct(Id))
   from
       `sandbox-first-project-1.bellabeat.weightlog` 
   
   ````
Query result: (no.of unique users according to id's)
``` 
   dailyactivity_Ids    33
   sleepday_Ids   	24
   heartrate_Ids	14 
   weightlog_Ids         8

```
- Summarizing overall data
  ```
      select 
       count(distinct(Id)) as Ids,
       avg(cast(TotalDistance as float64)) as average_of_total_distance,
       round(avg(cast(calories as int64))) as calories,
       round(avg(cast(LightlyActiveMinutes as int64))) as average_of_lightly_active_minutes,
       round(avg(cast(FairlyActiveMinutes as int64))) as average_fairly_active_minutes,
       round(avg(cast(VeryActiveMinutes as int64))) as average_of_very_active_minutes,
       round(avg(cast(TotalSteps as int64))) as daily_average_steps,
       max(cast(TotalSteps as int64))as maximum_daily_steps,
       min(cast(TotalSteps as int64))as minimum_daily_steps
   from
      `sandbox-first-project-1.bellabeat.daily_activity`;
   select
       (avg(cast(totalminutesasleep as float64))/60) as average_daily_sleep,
       (max(cast(totalminutesasleep as float64))/60) as maximum_daily_sleep,
       (min(cast(totalminutesasleep as float64))/60) as minimum_daily_sleep
   from
    `sandbox-first-project-1.bellabeat.sleep_day`

  ```
  Query result:
  ```
  
  Ids: 33
  average_of_total_distance: 5.489702121915415
  calories: 2304.0
  average_of_lightly_active_minutes: 193.0
  average_fairly_active_minutes: 14.0
  average_of_very_active_minutes: 21.0
  daily_average_steps: 7638.0
  maximum_daily_steps: 36019
  minimum_daily_steps: 0

  ```
  
  



  
  


