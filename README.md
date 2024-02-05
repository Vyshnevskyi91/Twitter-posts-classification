# <p align="center"><b>Patents-per-year-prediction</b></p>

![](https://th.bing.com/th/id/R.019d61d420fd85de87d1f013d9f89762?rik=UpY1vmSOe8wLww&riu=http%3a%2f%2fkeimeigakkan-h.ed.jp%2fwordpress%2fwp-content%2fuploads%2f2021%2f05%2fmy_0724twitter05.jpg&ehk=G5uYYB7qjgrRP0Kv4wV4FHr%2bvixV6TMn0KYa1rp3QjI%3d&risl=&pid=ImgRaw&r=0)

## Exploratory Data Analisys

### Import dataset from database

| tweet_id           | airline_sentiment | airline_sentiment_confidence | negativereason         | negativereason_confidence | airline   | airline_sentiment_gold | name        | negativereason_gold | retweet_count | text                                                                                                                                       | tweet_coord | tweet_created              | tweet_location    | user_timezone               |
|-------------------:|:------------------:|-----------------------------:|:-----------------------|:--------------------------:|:---------:|:------------------------:|:------------:|:---------------------:|--------------:|:-------------------------------------------------------------------------------------------------------------------------------------------:|:-----------:|:---------------------------:|:------------------:|:----------------------------:|
| 567588278875213824 | neutral            |                            1 |                        |                           |   Delta   |                          | JetBlueNews |                       |             0 | @JetBlue's new CEO seeks the right balance to please passengers and Wall ... - Greenfield Daily Reporter http://t.co/LM3opxkxch              |             | 2015-02-16 23:36:05 -0800 | USA               | Sydney                      |
| 567590027375702016 | negative           |                            1 | Can't Tell             |                        0.6503 |   Delta   |                          | nesi_1992   |                       |             0 | @JetBlue is REALLY getting on my nerves !! 😡😡 #nothappy                                                                                  |             | 2015-02-16 23:43:02 -0800 | undecided         | Pacific Time (US & Canada) |
| 567591480085463040 | negative           |                            1 | Late Flight            |                     0.346   |  United   |                          | CPoutloud   |                       |             0 | @united yes. We waited in line for almost an hour to do so. Some passengers just left not wanting to wait past 1am.                        |             | 2015-02-16 23:48:48 -0800 | Washington, DC    |                              |
| 567592368451248130 | negative           |                            1 | Late Flight            |                            1 |  United   |                          | brenduch    |                       |             0 | @united the we got into the gate at IAH on time and have given our seats and closed the flight. If you know people is arriving, have to wait |             | 2015-02-16 23:52:20 -0800 |                  | Buenos Aires                |
| 567594449874587648 | negative           |                            1 | Customer Service Issue |                        0.3451 | Southwest |                          | VahidESQ    |                       |             0 | @SouthwestAir its cool that my bags take a bit longer, dont give me baggage blue balls-turn the carousel on, tell me it's coming, then not.  |             | 2015-02-17 00:00:36 -0800 | Los Angeles, CA   | Pacific Time (US & Canada) |

### Checking number of values in df
United            3822  
US Airways        2913  
American          2604   
Southwest         2420  
Delta             2222  
Virgin America     504  
Name: airline, dtype: int64
### Grouping Negative feedback by airlines in new dataframe
airline  
American          1864  
Delta              955  
Southwest         1186  
US Airways        2263  
United            2633  
Virgin America     181  
Name: airline, dtype: int64
### Reason of negative feedback
|                      |           |
|----------------------|-----------|
|Customer Service Issue|        811|
|                      |        650|
|Late Flight           |        453|
|Can't Tell            |        246|
|Cancelled Flight      |        189|
|Lost Luggage          |        154|
|Flight Attendant Complaints|   123|
|Flight Booking Problems|       122|
|Bad Flight            |        104|
|longlines             |         50|
|Damaged Luggage       |         11|
Name: negativereason, dtype: int64
## Data Visualization
<img src="Bar_Plot.jpg" alt="Bar Plot" width="2000"/>

## Training Support Vector Machine

SVM Results:  
Accuracy: 0.7566448049706593  
Confusion Matrix:  
[1537  178   68]  
[ 225  333   65]  
[  97   72  322]  
Classification Report:  
```
            precision    recall  f1-score   support
```            
    negative       0.83      0.86      0.84      1783
     neutral       0.57      0.53      0.55       623
    positive       0.71      0.66      0.68       491

    accuracy                           0.76      2897
   macro avg       0.70      0.68      0.69      2897
weighted avg       0.75      0.76      0.75      2897
