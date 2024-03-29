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

<img width="1155" alt="截屏2024-01-29 17 38 26" src="https://github.com/qinxinLiu/PWC-Forge-Job-Simulation-Task-1-Call-Center-Trend/assets/67852322/e65270c7-4771-4d06-ab19-de1f91f22b60">

<img width="1156" alt="截屏2024-01-29 17 38 38" src="https://github.com/qinxinLiu/PWC-Forge-Job-Simulation-Task-1-Call-Center-Trend/assets/67852322/f904daa9-9340-480f-aa7a-c9e549cd8e54">


## 5. Insights

**CUSTOMER SATISFACTION**
- 40.46% of customers were satisfied with the calls by rating at 4 or 5, the average rating is at 2.76.
- The most common topics that customers called for were Streaming, Technical Support, and Payment related problems.
- Performance rating had been decreased from January to March.
- The majority of calls come in the morning.
- Overall, the Streaming topic had the highest rating.
- The number of abandoned calls had a downward trend for three months
- The call volume peaked on Monday and Saturday
- January had the largest percentage of issues handled, while February saw a decrease. In March, it went up once again.

**AGENT PERFORMANCE**
- Average speed of answering calls increased from January to March
- The number of unresolved calls gradually decrease over the three months.
- Becky has the best performance on answering `Streaming` and `Payment` related questions, Jim performs the best on`Admin` and `Contract` related questions while Dan perform the best on `Technical Support` .
- Becky also has the fastest average speed of answer among all and Marsha has the highest customer rating.
