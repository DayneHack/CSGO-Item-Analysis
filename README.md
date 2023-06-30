# Analysis of Counter Strike Global Offensive Weapon Skins and Their Prices
* In this project I explore the weapon skins of the primary 3 rifles in CSGO and try to determine if it is possible to accurately predict the price of a skin based off of multiple factors.

## What Are CS:GO Weapon Skins?
* CS:GO skins are collectible, cosmetic enhancements to the weapons that you can equip and use in game.
* Each skin has a float value which determines its condition (how worn/scraped it looks).
* Skins also have different rarity's which determine how likely you are to recieve one from opening a container or getting one as a drop.
* Skins are tradeable between players and can also be bought and sold on the Steam Market

## Project Overview
* Looked at all of the skins of the primary 3 rifles and attempted to see if their price correlates to their rarity, condition, and release year.
* Data was pulled from the Steam Market API and cleaned to isolate the variables I wanted to explore.
* Exploratory data Analysis looking to find a correlation between a skin's average price and its rarity, condition, and release year.
* Built and optimized models using Linear Regression and Random Forest to attempt to predict a skins price.

## Resources
**Python Version:** 3.9
**Packages:** pandas, seaborn, sklearn, numpy, matplotlib, requests, json, time
**Steam Market API:** https://steamapis.com/

## API
Pulled data from the Steam Market API (above) for the AK-47, M4A4, and M4A1-S weapon skins. For each skin we got the following information:
* Market name
* description
* Average prices of the past 15 days
* Which collection it comes from
* Rarity

## Data Cleaning
After puling the data, there was a lot of unnecessary information and a lot to clean up to be usable in a regression model. I made the following changes:
* Parsed the collection name out of the description
* Calculated an average price based off of the past 15 days
* Made a new column and parsed the weapon type from the skin name
* Made a new column and parsed out when a skin was last sold on the steam market
* Dropped all rows which did not have a sale on the market this year
* Made a new column and parsed condition from market name
* Made a new column and parsed the skin name from the market name
* Made a new column and mapped the collection with its release date
* Parsed the rarity from the messy rarity string

## Exploratory Data Analysis
I made a correlation graph as well of graphs of pivot tables to see the average price of skins accounting for their 
weapon type, rarity, and 
condition. Below are a few highlights.
![alt text](https://github.com/DayneHack/CSGO-Item-Analysis/blob/main/1.png?raw=true)
![alt text](https://github.com/DayneHack/CSGO-Item-Analysis/blob/main/2.png?raw=true)
![alt text](https://github.com/DayneHack/CSGO-Item-Analysis/blob/main/3.png?raw=true)
![alt text](https://github.com/DayneHack/CSGO-Item-Analysis/blob/main/4.png?raw=true)
![alt text](https://github.com/DayneHack/CSGO-Item-Analysis/blob/main/5.png?raw=true)
![alt text](https://github.com/DayneHack/CSGO-Item-Analysis/blob/main/6.png?raw=true)

## Model Building
I transformed the categorical variables into dummy variables then I split the data into train and test sets.

I then built two different models and evaluated them using the mean absolute error to easily interpret how far off the model is in predicting a skin's price.
The two models I used are Linear Regression and Random Forest

## Model Performance

* Linear Regression: 121.75
* Random Forest: 110.42

Neither model performed very well. Random Forest was the most accurate but is still off by 110. 

## Conclusion
My conclusion is that it is not possible to predict the price of a CS:GO weapon skin based off of factors such as release year, rarity, and condition.
