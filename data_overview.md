# Data overview, integrity check and cleaning process
The results of the survey are stored in the csv file with 10000 distinct rows, each row stands for an individual responder entire questionnaire. Some of the questions represent scales. Each scale in a question has its own column e.g. Q8_scale_1, Q8_scale_2 etc.

The number of respondent is evenly distributed between countries, with only Belgium and Ireland having 500 respondents. The variety on age and age segment is also representative and doesn't produce bias.
You can check the proportion and numbers using this query. Here I checked the proportion between countries but the same syntax can be used for other criterias as well.

```
SELECT city, count(city) as number_of_respondents ,MIN(country) AS country_id 
FROM `covid-19-aftermath.cvd_aftermath.raw_data`
GROUP BY City
ORDER BY MIN(country)
```
The naming conventions for the columns were a bit inconsistent. Sometimes the whole questions is written into the header row e.g "Do_you_work_from_home?_"

The datatypes in some columnn are inconsistent with some of the columns being STRING instead of INTEGER. The reason for that being the "N/A" value in some columns. I later changed those values to "0" in order to make calculations.
After trimming the dataset, checking the duplicates, and changing the values for consistency of the datatypes I downloaded the clean data back for the analysis.
