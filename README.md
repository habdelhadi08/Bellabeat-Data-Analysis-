# Bellabeat-Data-Analysis-
My data analysis for Bellabeat company
This is my FitBit data analysis using R, for my Google Data Analytics Capstone. 
FitBit-Data Analysis

Introduction and background
Urška Sršen and Sando Mur founded Bellabeat, a high-tech company that manufactures health-focused smart
products.Sršen used her background as an artist to develop beautifully designed technology that informs and inspires
women around the world. Collecting data on activity, sleep, stress, and reproductive health has allowed Bellabeat to
empower women with knowledge about their own health and habits. Sršen knows that an analysis of Bellabeat’s
available consumer data would reveal more opportunities for growth. She has asked the marketing analytics team to
focus on a Bellabeat product and analyze smart device usage data in order to gain insight into how people are already
using their smart devices. Then, using this information,she would like high-level recommendations for how these
trends can inform Bellabeat marketing strategy. Sršen wants to analyze smart device usage data in order to gain insight
into how consumers use non-Bellabeat smart devices. She then wants to select one Bellabeat product to apply these
insights to in the presentation.

Bellabeat-Data-Analysis
My data analysis for Bellabeat company.
Ask
Business Task: Identify potential opportunities for growth and recommendations for the Bellabeat marketing strategy
improvement based on trends in smart device usage.
Stakeholders: Bellabeat founded by Urška Sršen and Sando Mur, Bellabeat is a high-tech company that manufactures
health-focused smart products. Bellabeat is a women’s wellness company that has helped millions of women track their
cycle, pregnancies, and live more in sync with their cycles.
Prepare
The data was pulled from link. The data set contains personal fitness tracker from thirty fitbit users. Thirty eligible
Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity,
heart rate, and sleep monitoring. It includes information about daily activity, steps, and heart rate that can be used to
explore users’ habits. The dataset contains of two different timeframes 3/12/16 to 4/11/16 and 4/12/16 to 5/12/16.
Since the latter has more daily data we will be using the data from 4/12/16 to 5/12/16.
Upload your CSV files to R
data(package = .packages(all.available = TRUE))
Process
Installing and loading common packages and libraries Install and load the tidyverse
install.packages(&#39;tidyverse&#39;)

## Installing package into &#39;/cloud/lib/x86_64-pc-linux-gnu-library/4.3&#39;
## (as &#39;lib&#39; is unspecified)
library(tidyverse)
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr 1.1.2 ✔ readr 2.1.4
## ✔ forcats 1.0.0 ✔ stringr 1.5.0
## ✔ ggplot2 3.5.1 ✔ tibble 3.2.1
## ✔ lubridate 1.9.2 ✔ tidyr 1.3.0
## ✔ purrr 1.0.1
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag() masks stats::lag()
## ℹ Use the conflicted package (&lt;http://conflicted.r-lib.org/&gt;) to force all conflicts to become
errors
Load your CSV files Create a dataframe named ‘daily_activity’ and read in one of the CSV files from the dataset.
Remember, you can name your dataframe *
daily_activity &lt;- read.csv(&quot;dailyActivity_merged.csv&quot;)
Create another dataframe for the sleep data
sleep_day &lt;- read.csv(&quot;sleepDay_merged.csv&quot;)
Create another dataframe for the weight data
weight &lt;- read.csv(&quot;weightLogInfo_merged.csv&quot;)
Explore a few key tables Take a look at the daily_activity data
head(daily_activity)
## Id ActivityDate TotalSteps TotalDistance TrackerDistance
## 1 1503960366 4/12/2016 13162 8.50 8.50
## 2 1503960366 4/13/2016 10735 6.97 6.97
## 3 1503960366 4/14/2016 10460 6.74 6.74
## 4 1503960366 4/15/2016 9762 6.28 6.28
## 5 1503960366 4/16/2016 12669 8.16 8.16
## 6 1503960366 4/17/2016 9705 6.48 6.48
## LoggedActivitiesDistance VeryActiveDistance ModeratelyActiveDistance
## 1 0 1.88 0.55
## 2 0 1.57 0.69
## 3 0 2.44 0.40
## 4 0 2.14 1.26
## 5 0 2.71 0.41
## 6 0 3.19 0.78
## LightActiveDistance SedentaryActiveDistance VeryActiveMinutes
## 1 6.06 0 25
## 2 4.71 0 21
## 3 3.91 0 30
## 4 2.83 0 29
## 5 5.04 0 36
## 6 2.51 0 38
## FairlyActiveMinutes LightlyActiveMinutes SedentaryMinutes Calories
## 1 13 328 728 1985
## 2 19 217 776 1797
## 3 11 181 1218 1776
## 4 34 209 726 1745
## 5 10 221 773 1863
## 6 20 164 539 1728

Identify all the columns in the daily_activity data
colnames(daily_activity)
## [1] &quot;Id&quot; &quot;ActivityDate&quot;
## [3] &quot;TotalSteps&quot; &quot;TotalDistance&quot;
## [5] &quot;TrackerDistance&quot; &quot;LoggedActivitiesDistance&quot;
## [7] &quot;VeryActiveDistance&quot; &quot;ModeratelyActiveDistance&quot;
## [9] &quot;LightActiveDistance&quot; &quot;SedentaryActiveDistance&quot;
## [11] &quot;VeryActiveMinutes&quot; &quot;FairlyActiveMinutes&quot;
## [13] &quot;LightlyActiveMinutes&quot; &quot;SedentaryMinutes&quot;
## [15] &quot;Calories&quot;
Take a look at the sleep_day data
head(sleep_day)
## Id SleepDay TotalSleepRecords TotalMinutesAsleep
## 1 1503960366 4/12/2016 12:00:00 AM 1 327
## 2 1503960366 4/13/2016 12:00:00 AM 2 384
## 3 1503960366 4/15/2016 12:00:00 AM 1 412
## 4 1503960366 4/16/2016 12:00:00 AM 2 340
## 5 1503960366 4/17/2016 12:00:00 AM 1 700
## 6 1503960366 4/19/2016 12:00:00 AM 1 304
## TotalTimeInBed
## 1 346
## 2 407
## 3 442
## 4 367
## 5 712
## 6 320
Identify all the columns in the daily_activity data
colnames(sleep_day)
## [1] &quot;Id&quot; &quot;SleepDay&quot; &quot;TotalSleepRecords&quot;
## [4] &quot;TotalMinutesAsleep&quot; &quot;TotalTimeInBed&quot;
Take a look at the weight data
head(weight)
## Id Date WeightKg WeightPounds Fat BMI
## 1 1503960366 5/2/2016 11:59:59 PM 52.6 115.9631 22 22.65
## 2 1503960366 5/3/2016 11:59:59 PM 52.6 115.9631 NA 22.65
## 3 1927972279 4/13/2016 1:08:52 AM 133.5 294.3171 NA 47.54
## 4 2873212765 4/21/2016 11:59:59 PM 56.7 125.0021 NA 21.45
## 5 2873212765 5/12/2016 11:59:59 PM 57.3 126.3249 NA 21.69
## 6 4319703577 4/17/2016 11:59:59 PM 72.4 159.6147 25 27.45
## IsManualReport LogId
## 1 True 1.462234e+12
## 2 True 1.462320e+12
## 3 False 1.460510e+12
## 4 True 1.461283e+12
## 5 True 1.463098e+12
## 6 True 1.460938e+12
Identify all the columns in the weight data
colnames(weight)
## [1] &quot;Id&quot; &quot;Date&quot; &quot;WeightKg&quot; &quot;WeightPounds&quot;
## [5] &quot;Fat&quot; &quot;BMI&quot; &quot;IsManualReport&quot; &quot;LogId&quot;

All datasets have Id, this can be used to merge the datasets. Merging these two datasets together
combined_data &lt;- merge(sleep_day, daily_activity, by=&quot;Id&quot;)
combined_data1 &lt;- merge(weight, daily_activity, by=&quot;Id&quot;)
Let`s take a look at how many participants are in each data set.
n_distinct(combined_data$Id)
## [1] 24
head(combined_data)
## Id SleepDay TotalSleepRecords TotalMinutesAsleep
## 1 1503960366 4/12/2016 12:00:00 AM 1 327
## 2 1503960366 4/12/2016 12:00:00 AM 1 327
## 3 1503960366 4/12/2016 12:00:00 AM 1 327
## 4 1503960366 4/12/2016 12:00:00 AM 1 327
## 5 1503960366 4/12/2016 12:00:00 AM 1 327
## 6 1503960366 4/12/2016 12:00:00 AM 1 327
## TotalTimeInBed ActivityDate TotalSteps TotalDistance TrackerDistance
## 1 346 5/7/2016 11992 7.71 7.71
## 2 346 5/6/2016 12159 8.03 8.03
## 3 346 5/1/2016 10602 6.81 6.81
## 4 346 4/30/2016 14673 9.25 9.25
## 5 346 4/12/2016 13162 8.50 8.50
## 6 346 4/13/2016 10735 6.97 6.97
## LoggedActivitiesDistance VeryActiveDistance ModeratelyActiveDistance
## 1 0 2.46 2.12
## 2 0 1.97 0.25
## 3 0 2.29 1.60
## 4 0 3.56 1.42
## 5 0 1.88 0.55
## 6 0 1.57 0.69
## LightActiveDistance SedentaryActiveDistance VeryActiveMinutes
## 1 3.13 0 37
## 2 5.81 0 24
## 3 2.92 0 33
## 4 4.27 0 52
## 5 6.06 0 25
## 6 4.71 0 21
## FairlyActiveMinutes LightlyActiveMinutes SedentaryMinutes Calories
## 1 46 175 833 1821
## 2 6 289 754 1896
## 3 35 246 730 1820
## 4 34 217 712 1947
## 5 13 328 728 1985
## 6 19 217 776 1797
n_distinct(combined_data1$Id)
## [1] 8
head(combined_data1)
## Id Date WeightKg WeightPounds Fat BMI
## 1 1503960366 5/2/2016 11:59:59 PM 52.6 115.9631 22 22.65
## 2 1503960366 5/2/2016 11:59:59 PM 52.6 115.9631 22 22.65
## 3 1503960366 5/2/2016 11:59:59 PM 52.6 115.9631 22 22.65
## 4 1503960366 5/2/2016 11:59:59 PM 52.6 115.9631 22 22.65
## 5 1503960366 5/2/2016 11:59:59 PM 52.6 115.9631 22 22.65
## 6 1503960366 5/2/2016 11:59:59 PM 52.6 115.9631 22 22.65

## IsManualReport LogId ActivityDate TotalSteps TotalDistance
## 1 True 1.462234e+12 4/16/2016 12669 8.16
## 2 True 1.462234e+12 4/18/2016 13019 8.59
## 3 True 1.462234e+12 4/15/2016 9762 6.28
## 4 True 1.462234e+12 5/8/2016 10060 6.58
## 5 True 1.462234e+12 4/17/2016 9705 6.48
## 6 True 1.462234e+12 4/19/2016 15506 9.88
## TrackerDistance LoggedActivitiesDistance VeryActiveDistance
## 1 8.16 0 2.71
## 2 8.59 0 3.25
## 3 6.28 0 2.14
## 4 6.58 0 3.53
## 5 6.48 0 3.19
## 6 9.88 0 3.53
## ModeratelyActiveDistance LightActiveDistance SedentaryActiveDistance
## 1 0.41 5.04 0
## 2 0.64 4.71 0
## 3 1.26 2.83 0
## 4 0.32 2.73 0
## 5 0.78 2.51 0
## 6 1.32 5.03 0
## VeryActiveMinutes FairlyActiveMinutes LightlyActiveMinutes SedentaryMinutes
## 1 36 10 221 773
## 2 42 16 233 1149
## 3 29 34 209 726
## 4 44 8 203 574
## 5 38 20 164 539
## 6 50 31 264 775
## Calories
## 1 1863
## 2 1921
## 3 1745
## 4 1740
## 5 1728
## 6 2035
Analyze
Understanding some summary statistics: Let`s check how many unique participants are there in each dataframe.
n_distinct(daily_activity$Id)
## [1] 33
n_distinct(sleep_day$Id)
## [1] 24
n_distinct(weight$Id)
## [1] 8
It looks like there may be more participants in the daily activity dataset than the sleep dataset and the weight dataset.
Let`s check how many observations are there in each dataframe.
nrow(daily_activity)
## [1] 940
nrow(sleep_day)
## [1] 413

nrow(weight)
## [1] 67
Quick summary statistics we’d want to know about each data frame for the daily activity: dataframe:
combined_data %&gt;%
select(TotalSteps,
TotalDistance,
SedentaryMinutes) %&gt;%
summary()
## TotalSteps TotalDistance SedentaryMinutes
## Min. : 0 Min. : 0.000 Min. : 0.0
## 1st Qu.: 4660 1st Qu.: 3.180 1st Qu.: 659.0
## Median : 8596 Median : 6.120 Median : 734.0
## Mean : 8117 Mean : 5.735 Mean : 799.2
## 3rd Qu.:11317 3rd Qu.: 7.920 3rd Qu.: 853.0
## Max. :22988 Max. :17.950 Max. :1440.0
Based on this summary an average user walks 5.490 km or 7638 steps a day. The average of SendentaryMinutes is
991.2.
For the sleep dataframe:
sleep_day %&gt;%
select(TotalSleepRecords,
TotalMinutesAsleep,
TotalTimeInBed) %&gt;%
summary()
## TotalSleepRecords TotalMinutesAsleep TotalTimeInBed
## Min. :1.000 Min. : 58.0 Min. : 61.0
## 1st Qu.:1.000 1st Qu.:361.0 1st Qu.:403.0
## Median :1.000 Median :433.0 Median :463.0
## Mean :1.119 Mean :419.5 Mean :458.6
## 3rd Qu.:1.000 3rd Qu.:490.0 3rd Qu.:526.0
## Max. :3.000 Max. :796.0 Max. :961.0
Based on this summary the average of TotalMinutesAseep is 419.5 and the average TotalTimeInBed is 458.6. They
correlate with each other.
combined_data %&gt;%
select(TotalSteps,
Calories,
VeryActiveDistance) %&gt;%
summary()
## TotalSteps Calories VeryActiveDistance
## Min. : 0 Min. : 0 Min. : 0.000
## 1st Qu.: 4660 1st Qu.:1783 1st Qu.: 0.000
## Median : 8596 Median :2162 Median : 0.530
## Mean : 8117 Mean :2329 Mean : 1.399
## 3rd Qu.:11317 3rd Qu.:2865 3rd Qu.: 2.310
## Max. :22988 Max. :4900 Max. :13.400
Based on this summary the average TotalSteps is 8117 and the average Calories is 2329.
Share / Visualization
Plotting a few explorations Let`s explore the relationship between steps taken in a day and sedentary minutes.
ggplot(data= combined_data, aes(x=SedentaryMinutes, y=TotalMinutesAsleep)) +
geom_point(colour=&quot;Chocolate1&quot;) + geom_smooth(color = &quot;cadetblue4&quot;)+

labs(title=&quot;Correlation Between Sedentary Time and Time Asleep&quot;)
## `geom_smooth()` using method = &#39;gam&#39; and formula = &#39;y ~ s(x, bs = &quot;cs&quot;)&#39;

The scatter plot above shows that between 0- 1500 SedentaryMinutes vs. TotalMinutesAsleep. Let`s explore the
relationship between minutes asleep and time in bed. There is a correlation between the x axes and the y axes.
ggplot(data=sleep_day, aes(x=TotalMinutesAsleep, y=TotalTimeInBed, color=&quot;red&quot;)) + geom_point()+
labs(title = &quot;TotalMinutesAsleep vs TotalTimeInBed&quot;)

The scatter plot shows as TotalMinutesAsleep increese TotlaTimeInBed increases as well.
Now let’s explore some different relationships between activity and sleep as well. For example, what is the relationship
between TotalSteps and TotalMinutesAsleep?

ggplot(data=combined_data, aes(x=TotalTimeInBed, y=TotalSteps))+ geom_histogram(stat = &quot;identity&quot;,
fill=&#39;darkblue&#39;) +
theme(axis.text.x = element_text(angle = 90)) +
labs(title = &quot;Relationship between TotalMinutesAsleep vs TotalSteps&quot;)
## Warning in geom_histogram(stat = &quot;identity&quot;, fill = &quot;darkblue&quot;): Ignoring
## unknown parameters: `binwidth`, `bins`, and `pad`

Based on this graph we can see when users have a good average sleep, they are more active.
Let’s explore the relationship between VeryActiveDistance and Calories:
ggplot(data=combined_data1, aes(x=VeryActiveDistance, y=Calories, color=&quot;purple&quot;)) + geom_smooth()+
labs(title = &quot;VeryActiveDistance vs Calories&quot;)
## `geom_smooth()` using method = &#39;gam&#39; and formula = &#39;y ~ s(x, bs = &quot;cs&quot;)&#39;

Based on the plot, it shows positive relationship between Calories and VeryActiveDistance. As VeryActiveDistance
increase Calories increases as well.
Act/ Reccomendation:
Bellabeat did a great job representing its data, however here is my recommendations to improve their sales:
• The data should should the gender of each user. This will enable us to see which gender we should target.
• Bellabeat should include some diet plans based on the user’s weight. This will enhance their performance
• Bellabeat should include more participates. This way we will have larger set of data, which will help data analyst
to gather more information about the participants.
• Based on the analysis there are fewer participants in the weight dataframe. The company should have more
participant to correlated better with the other dataframs.
• The company can create personalize plans for users, based on their daily activity and weight. They will
encourage more users to try the product.

Thank you for your interest in my FitBit case study!
