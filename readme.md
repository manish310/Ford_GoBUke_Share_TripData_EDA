#  Analysis of Ford GoBike Trip Dataset
## by Manish Kumar


## Dataset

> Ford GoBike is bicycle sharing service operational in San Francisco Bay Area.It began operation in June 28, 2017.The company provides bike trip information for data analysis perposes. For the current analysis, I have selected one year data from January, 2018 to December 2018.The dataset contains 16 columns and 18,63,721 rows. I hope analysis of one year data will result in some good insights.
Columns are as follows:
duration_sec               int64
start_time                 object
end_time                   object
start_station_id           float64
start_station_name         object
start_station_latitude     float64
start_station_longitude    float64
end_station_id             float64
end_station_name           object
end_station_latitude       float64
end_station_longitude      float64
bike_id                    int64
user_type                  object
member_birth_year          float64
member_gender              object
bike_share_for_all_trip    object

>Before starting analysis, I need to wrangle the dataset.Wrangling Efforts:
 1. Two columns start_time and end_time is in string type that I need to change into datetime. This change will enable me to use various datetime function and extract useful information from it.
 2. member_birth_year,start_station_id and end_station_id are float type. As these columns are integer only better I will change it to Int type.
 3. member_birth_year column is there in dataset originally.As I need to deal with age more frequntly better I will create a separate column 'age'.
 4. Distance between to station or travelled distance in a trip is not given in dataset. However,    
 start_station_latitude,start_station_longitude,end_station_latitude and end_station_longitude are given, using this infomation I can calculate geo_distance between two staions in Kms. Later, through analysis I can check if this distance has any relation with other columns in the dataset. 
 5. I used columns age and time(Hours,0-24) to create two categorical columns 'Time_category' and 'age_group', which will make exploratory analysis much easy.
 6. I added few more columns tripid, month and weekday. These columns will be quite handy during exploratory analysis.

## Summary of Findings

> Following are key findings:
1. Station "San Francisco Caltrain Station 2(Townsend St at 4th St)" is the Busiest one.
2. The most popular trip is :San Francisco Ferry Building (Harry Bridges Plaza) To The Embarcadero at Sansome St
2. Weekadays have more trips than weekends.
2. A particular day morning and evening are busy hours except sunday and saturday.
3. Male are leading in long distance trip and among them millenials.
4. Millenials(18-34) are the most frequent rider in Ford GoBike sharing system.
5. Morning rides are having more trip duration time.
6. User type 'Customer' type has quite low share compare to 'Subscriber'.
7. Segregeting monthwise trip frequency based on gender category shows 'Male' had most of the share.
8. Bike_share_for_All subscribers are more likely use this system in the afternoon or evening compared to normal subscribers which prefer morning time.
9. At day level, if I see then Morning, Evening and Afternoon are pick time. If I see age wise the millenials(18-34) are major section which are using bike share service. Now moving to user type, Subscribers those belongs to millenials age group are using the bike share service most and their pick time is morning and evening. This trends is persist in further classication on gender basis. In contrast, Most Customers belongs to millenials age group but pick time is evening and afternoon.This trends is persist in further classication on gender basis.

## Key Insights for Presentation

### 1. The most busiest station - San Francisco Caltrain Station 2(Townsend St at 4th St)

>"San Francisco Caltrain Station 2(Townsend St at 4th St)" is the busiest one.The analysis is based on the most number of incoming and outgoing rides to or from a station.

### 2. The Relation: Trip Duration Vs Trip Distance.

> There is a linear relation with positive slope between trip distance and trip duration as shown by regression line. This means for majority of trips, which are of longer distance more time is taken.This also shows the the distance calculated using latitude and longitude is quite reaosnable.However, for same distance customers have taken longer trip time compared to Subscribers. One possible reason might be that Customers are using this explore the city rather than for daily works.A possbile further analysis would be to see effect of categorical variable(Gender, Age, Time, User Type) on this relation.

### 3. How is response of the program Bike for share for All?
>Bike share for All is an unique program launched by Ford Gobike syatem. Bike Share for All provides a one-time $5 annual membership for qualifying residents. The program also includes a cash payment option for those who do not have a debit or credit card. As per website eligibility to enroll this program is "Bike Share for All is available to Bay Area residents ages 18 and older who qualify for Calfresh, SFMTA (Low Income) Lifeline Passes or PG&E CARE utility discount."
I can see Bike_share_for_All subscribers have different trends than normal subscribers.Bike_share_for_All subscribers are more likely use this system in the afternoon or evening compared to normal subscribers which prefer morning time.

### 4. Trends of trip count based on Gender, User Type, Age Group and Time Category
> This is sort of summarisation of key findings in previous analysis and reinforce it. At day level, if I see then Morning, Evening and Afternoon are pick time. If I see age wise the millenials(18-34) are major section which are using bike share service. Now moving to user type, Subscribers those belongs to millenials age group are using the bike share service most and their pick time is morning and evening. This trends is persist in further classication on gender basis. In contrast, Most Customers belongs to millenials age group but pick time is evening and afternoon.This trends is persist in further classication on gender basis.

#### Reference:
>  
1. https://stackoverflow.com/questions/4913349/haversine-formula-in-python-bearing-and-distance-between-two-gps-points
2. https://janakiev.com/blog/gps-points-distance-python/
3. https://engineering.upside.com/a-beginners-guide-to-optimizing-pandas-code-for-speed-c09ef2c6a4d6
4. http://robertmitchellv.com/blog-bar-chart-annotations-pandas-mpl.html
5. https://www.dataquest.io/blog/pandas-pivot-table/