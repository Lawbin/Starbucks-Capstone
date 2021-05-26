# Starbucks Capstone Challenge

## Challenge Introduction
This data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks.

Not all users receive the same offer, and that is the challenge to solve with this data set.

The task is to combine transaction, demographic and offer data to determine which demographic groups respond best to which offer type. This data set is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products.

Every offer has a validity period before the offer expires. As an example, a BOGO offer might be valid for only 5 days. You'll see in the data set that informational offers have a validity period even though these ads are merely providing information about a product; for example, if an informational offer has 7 days of validity, you can assume the customer is feeling the influence of the offer for 7 days after receiving the advertisement.

We are given transactional data showing user purchases made on the app including the timestamp of purchase and the amount of money spent on a purchase. This transactional data also has a record for each offer that a user receives as well as a record for when a user actually views the offer. There are also records for when a user completes an offer.

## Problem Statement
Starbucks has about 32,660 stores across the globe. Within a month, 37.8 million Americans visited a Starbucks. With this many customers, there are a lot of data that Starbucks can use to promote their brand. By analyzing their customer behavior they can make decisions based on target audiences. Using customer, offer and transactional data Starbucks would like to gain insights and know the effectiveness of offers.

The objective is to build a machine learning model that predicts whether or not a customer will respond to an offer.

## Motivation
Looking at the brief, I set a goal of answering two questions:
1. What features influence customers the most in responding to an offer?
2. Can these features predict whether or not a customer will respond to an offer?

## Libraries
- `pandas`
- `numpy`
- `json`
- `sci-kit learn`
- `math`
- `matplotlib`
- `seaborn`
- `time`
- `datetime`

## Datasets
Three datasets were provided in the form of JSON files.

**profile.json**
Contains customer information.
  - gender: (categorical) M, F, O, or null
  - age: (int)
  - id: (string)
  - became_member_on: (date)
  - income: (float)

**portfolio.json**
Contains information about offers.
  - reward: (int) reward for completing an offer
  - channels: (list) web, email, mobile, social
  - difficulty: (int) minimum amount customer needs to spend to complete offer
  - duration: (string) offer valid period
  - offer_type: (string) bogo, discount, informational
  - id: (string)

**transcript.json**
Contains transactional events.
  - person: (string)
  - event: (string) offer received, offer viewed, transaction, offer completed
  - value: (dictionary) different values depending on the event type
    - offer id/offer_id: (string)
    - amount: (float) money spent in that event
    - reward: (int) reward for completing an offer
  - time: (int) hours after start of test
  
## Files
This repository contains 2 files. 
- `Starbucks_Capstone_notebook.ipynb` : Jupyter Notebook with analysis and machine learning model.
- `Data`:
    - 1. profile.json
    - 2. portfolio.json
    - 3. transcript.json

## Answer to Questions Above
### Question 1
How much a customer spends is the biggest influencer on whether or not they respond to an offer. By predicting and understanding how much a customer spends will boost offer response rate.

Membership duration (how long a customer has been a Starbucks Member) can also influence offer response. Long term members have experienced these types of offers in the past. Thus, they understand how they work and which ones are worth it. For a BOGO offer, the customer may save it for when they need to purchase more than one cup (with a companion) or if there was a popular promotional drink.

How offers are delivered to customers can also influence a customer's response. So assigning more quota to one medium may boost response rates.

Difficulty corresponds to how much a customer needs to spend in order to be able to use an offer. This can correlate to how much a customer spends. If difficulty is high and the offer is given to someone who does not spend a lot then they are less likely to respond.

Duration is how long an offer lasts, given more leeway in when they need to use an offer by can boost response rates. When an offer lasts longer there are more chances for a customer to have some occasion where they will go to Starbucks to make a purchase.

### Question 2
Using at least the 5 features discussed in question 1, it is feasible to use the data to predict if a customer will respond. It can also help improve the overall response rate.  I have achieved an 89% accuracy with a tuned RandomForestClassifier.

long with predicting if a customer responds to an offer, we can predict how much a customer will spend based on each offer. This coincides with how the feature "spending" influences the model.

Working in the advertising industry, there are many instances where I have to perform customer segmentation. Based on the data we have, if other than the 3 datasets given in this project. If we had access to other apps or content, then we can perform segmentation and create different persona groups. These groups would be based around demographics and/or content each customer is interested in. Simply, segementation based on products and behavior. This will allow Starbucks to target specific audiences to achieve a higher response rate.

## Acknowledgements
Thanks to Udacity for providing the necessary data.
