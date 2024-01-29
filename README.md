# PWC-Forge-Job-Simulation-Task-1-Call-Center-Trend
## 1. Problem Statement
An overview of long-term trends in customer and agent behaviour.
Create a dashboard in Power BI that reflects all relevant Key Performance Indicators (KPIs) and metrics in the dataset. 

Possible KPIs include (to get you started, but not limited to):

·  Overall customer satisfaction

·  Overall calls answered/abandoned

·  Calls by time

·  Average speed of answer

·  Agent’s performance quadrant -> average handle time (talk duration) vs calls answered

## 2. Data Preprocessing and Modelling

Call Center trends dataset contains **10** columns and **5000** rows of observation

Transform data in Power Query
·  Removing null values
·  Removing duplicates

## 3. Create Measures (DAX)

` · Total Calls = COUNTROWS('Call Center')`

`· Answered Call = CALCULATE(COUNT('Sheet1'[Answered (Y/N)]), 'Sheet1'[Answered (Y/N)]="Y")`

`· Unanswered Call = COUNT('Sheet1'[Call Id])-[Answered Call]`

`· Possitive satisfation rating = CALCULATE(COUNT('Call Center'[Satisfaction rating]), 'Call Center'[Satisfaction rating] IN {4,5})`

`· Overall Customer Satisfation = DIVIDE('Call Center'[Possitive satisfation rating], COUNT('Call Center'[Satisfaction rating]),0)`

`· Resolved Calls = COUNTX(FILTER('Call Center','Call Center'[Resolved] = "Y"), 'Call Center'[Resolved])`

`· Unresolved Calls = CALCULATE(COUNT('Call Center'[Resolved]), 'Call Center'[Resolved] = "N")`

`· Talk Duration in sec = MINUTE('Call Center'[AvgTalkDuration])*60 + SECOND('Call Center'[AvgTalkDuration])`

`· Month = MONTH('Call Center'[Date])`

`· Hour = HOUR('Call Center'[Time])`

## 4. Power BI Dashboard

![](截屏2024-01-29%2017.38.26.png)


## 5. Insights
