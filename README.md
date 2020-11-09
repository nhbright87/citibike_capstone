# citibike_usage_capstone
First Capstone Project examining CitiBike usage in NYC

CRISP-DM Methodology:
1. Business Understanding:
HYPOTHESIS:
I expect the total number of rides to be down for the year of 2020 compared to the corresponding months for the previous X years

Random Qs:
- # of Bikes/Stations in System
- Minimum Age?
- Default inputs?
- Setup Process

DETERMINATIVE STATS:
- Total # of Rides
- User Type Breakdown
- Avg Trip Duration
- Start/End Station Distribution

JUST FOR FUN STATS:
- Longest Ride
- Most Used Bike
- Gender/Age Breakdown

2. Data Understanding:
DATA STRUCTURE & TYPES: https://www.citibikenyc.com/system-data
15 Variables
- Trip Duration (Seconds): int
- Start Time & Date: obj
- Stop Time & Date: obj
- Start Station ID: int
- Start Station Name: obj
- Start Station Lat: float
- Start Station Long: float
- End Station ID: int
- End Station Name: obj
- End Station Lat: float
- End Station Long: float
- Bike ID: int
- User Type (Customer = 24/72-hour Pass, Subscriber = Annual Member): obj
- Birth Year: int
- Gender (0 = Unk, 1 = M, 2 = F): int

3. Data Preparation:
- When ingesting file, convert the 'starttime' column to the datetime format and set it as the index. This can be done in the parameters for the read_csv function.
- Add an age column by subtracting the 'birth year' from the 'data_year' object, which must be created and set manually for each year of the data
- After adding the 'age' column, filter out all ages over 100 and replace them with a NaN.
- The 'tripduration' column must also be cleaned to remove all rides longer than 3 hours (10800 seconds) and replacing them with a NaN.
- Unnecessary columns can now be removed. All that should remain in the DataFrame after this are the following columns:
  'tripduration', 'start station name', 'end station name', 'bikeid', 'usertype', 'age', 'gender'

4. Modeling:
I manually created a dataframe containing the total number of monthly rides for the relevant years. I got a monthly mean for 2017-2019 as well as the standard deviation across months for those years. The monthly totals for all years as well as the monthly average were plotted on a graph for visual evaluation.

5. Evaluation:
I compared the  monthly numbers for 2020 to the monthly averages based on the previous years and measured whether or not the 2020 data fell within the standard deviation from those monthly averages.

6. Deployment:
I plotted the 2020 monthly total, monthly average and monthly average +/- STD to determine how the numbers for 2020 measured up.