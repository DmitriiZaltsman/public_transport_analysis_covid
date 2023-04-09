# Defining the question
The main questions I asked was "Has the pandemic scared people who use public transport?" and "Has the pandemic changed the people's habits?"
In order to focus on the public transport the following route has been decided.

# Developing the stages

## Change in number of trips:
The task of this stage is to examine the change in the number of trips made by public transport goers after the COVID-19 pandemic started, and to identify any significant trends or patterns in the data. This will involve analyzing the survey responses related to the frequency of public transport use and comparing the results before and after the pandemic, with the aim of providing insights into the impact of COVID-19 on public transport ridership. Two groups of public transport users were put for this stage: the casual casual riders use public transport less than 2 days a week and frequent riders use the public transport more. Further stages will involve be analysing the frequent riders only.

Query for the frequent riders:
```
SELECT count(Q13_14_scale) as population, Q13_14_scale 
FROM `covid-19-aftermath.cvd_aftermath.clean_data_new`
WHERE Q8_14_scale between 4 and 5
GROUP BY Q13_14_scale
ORDER by population DESC
```
Query for casual riders:
```
SELECT count(Q13_14_scale) as population, Q13_14_scale 
FROM `covid-19-aftermath.cvd_aftermath.clean_data_new`
WHERE Q8_14_scale between 2 and 3
GROUP BY Q13_14_scale
ORDER by population DESC
LIMIT 1000
```

## Change in other habits:
This involves analyzing the survey responses related to changes in destination choices, mode of transportation, and peak hour avoidance. The analysis will aim to identify any shifts in travel patterns during the COVID-19 pandemic. I mainly focused on the frequent riders in order to gain insights that might help improve the public transport.

Query for changing destinations:
```
SELECT count(Q12_4) as population, Q12_4 
FROM `covid-19-aftermath.cvd_aftermath.clean_data_new`
WHERE Q8_14_scale between 4 and 5
GROUP BY Q12_4
LIMIT 1000
```
Most of the frequent riders haven't changed their destinations.

Modes of transportation:
```
SELECT count(Q12_2) as population, Q12_2 
FROM `covid-19-aftermath.cvd_aftermath.clean_data_new`
WHERE Q8_14_scale between 4 and 5
GROUP BY Q12_2
LIMIT 1000
```
Most of the frequent riders haven't changed the modes of transport.

Peak hour avoidance:
```
SELECT count(Q12_2) as population, Q12_2 
FROM `covid-19-aftermath.cvd_aftermath.clean_data_new`
WHERE Q8_14_scale between 4 and 5
GROUP BY Q12_2
LIMIT 1000
```

Most of the frequent riders haven't avoided peak hours.

## Reasoning behind the decrease in number of trips: 
The next stage of the analysis involves examining the factors that may be contributing to the decrease in the number of trips made by public transport goers. This will involve looking at the survey responses related to the reasons why people are using public transport less frequently. The analysis will aim to identify any common themes or patterns in the responses, such as concerns about the risk of exposure to COVID-19, changes in quality of public transport and switching to the remote form of work. By understanding the reasoning behind the decrease in public transport ridership, this stage of the analysis will provide valuable insights into the factors that are shaping the current transport landscape in the EU.

Fear for health:
```
SELECT count(Q14_1) as population, Q14_1 
FROM `covid-19-aftermath.cvd_aftermath.clean_data_new`
WHERE Q8_14_scale between 4 and 5
AND Q13_14_scale between 1 and 2
GROUP BY Q14_1
ORDER by population DESC
LIMIT 1000
```
Almost two thirds of the responders listed fear for their well-being as reason for making less trips.

Worsened quality of public transport services: 
```
SELECT count(Q14_2) as population, Q14_2
FROM `covid-19-aftermath.cvd_aftermath.clean_data_new`
WHERE Q8_14_scale between 4 and 5
AND Q13_14_scale between 1 and 2
GROUP BY Q14_2
ORDER by population DESC
LIMIT 1000
```
In the majority respondents do not list the drop in quality as the reason for making less trips.
Change to the remote format of work:
```
SELECT count(Q14_4) as population, Q14_4 
FROM `covid-19-aftermath.cvd_aftermath.clean_data_new`
WHERE Q8_14_scale between 4 and 5
AND Q13_14_scale between 1 and 2
GROUP BY Q14_4
ORDER by population DESC
LIMIT 1000
```
In the majority respondents do not list the switch to the remote work as the reason to make less trips. It should be mentioned though that it shows that not as many people could switch to the remote work overall.
## Comfort, accessibility and feedback
The final stage of the analysis involves examining the survey responses related to the feedback on the public transportation system, specifically on the frequency of service, availability of seats due to rules and regulations, and the accessibility of the system. This includes analyzing the responses related to the satisfaction level of the population regarding the frequency of service and accessibility of public transport, as well as the availability of seats for passengers. Additionally, this stage involves examining the responses related to the availability of seats due to COVID-19 rules and regulations.

The applied syntax is similar to one in the previous stage. The results show that overall people are comfortable with using the public transport in the future though there is a group of people which are wary of it.

The accessibility of public transport is very high, the feedback on public transport quality consists mostly of "No changes" and "has worsened" answers. It leads to a conclusion that should we eliminate the threat to public health and develop new ways to make the public transport safer, riders would feel more at ease in the future.

# Answering the first two questions

The pandemic surely had it's effect on the public making them decrease the number of the trips they take via public transport. Those who used it less frequently managed to decrease the number easier than those who rely on it as a frequent mode of transportation. 

Other than making less trips other habits regarding transportation didn't seem to change. From this information and the fact that overall people are comfortable with using public transport in the future. It can be suggested that most perceived the pandemic as a temporary period, 
