Starbucks Capstone Challenge - Data Analysis
## Introduction
​
This data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks.
​
Not all users receive the same offer, and that is the challenge to solve with this data set.
​
The task is to combine transaction, demographic and offer data to determine which demographic groups respond best to which offer type. This data set is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products.
​
Every offer has a validity period before the offer expires. As an example, a BOGO offer might be valid for only 5 days. You'll see in the data set that informational offers have a validity period even though these ads are merely providing information about a product; for example, if an informational offer has 7 days of validity, you can assume the customer is feeling the influence of the offer for 7 days after receiving the advertisement.
​
We are given transactional data showing user purchases made on the app including the timestamp of purchase and the amount of money spent on a purchase. This transactional data also has a record for each offer that a user receives as well as a record for when a user actually views the offer. There are also records for when a user completes an offer.
​
Keep in mind as well that someone using the app might make a purchase through the app without having received an offer or seen an offer.
​
#### Example
​
A user could receive a discount offer buy 10 dollars get 2 off on Monday. The offer is valid for 10 days from receipt. If the customer accumulates at least 10 dollars in purchases during the validity period, the customer completes the offer.
​
Customers do not opt into the offers that they receive; in other words, a user can receive an offer, never actually view the offer, and still complete the offer. For example, a user might receive the "buy 10 dollars get 2 dollars off offer", but the user never opens the offer during the 10 day validity period. The customer spends 15 dollars during those ten days. There will be an offer completion record in the data set; however, the customer was not influenced by the offer because the customer never viewed the offer.
​
## Datasets
​
**portfolio.json** (10 offers x 6 fields) - metadata for each offer (duration, type, etc.)
* id (str) - offer ID
* offer_type (str) - type of offer (BOGO, discount, informational)
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list[str]) - web, email, mobile, social
​
**profile.json** (17,000 users x 5 fields) - demographic data for each user
* age (int) - age of the customer (missing values are encoded as 118)
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (some entries contain 'O' for other rather than 'M' or 'F')
* id (str) - customer ID
* income (float) - customer's income
​
**transcript.json** (306,534 transactions x 4 fields)- records for events (transactions, offers received, offers viewed, and offers completed)
* event (str) - record description (transaction, offer received, offer viewed, etc.)
* person (str) - customer ID
* time (int) - time in hours since start of test (the data begins at time t = 0)
* value - (dict) - either an offer ID or transaction amount depending on the record


## Data Model <a name="Model"></a>
- After pre-processing the dataset and after visualization the next part is to make a model that figure out whether the customer responded to offer or not.

- Here we use six different types of models that will predict whether the customer responded to offer or not.

- To make a model we will split the data into features and target and also in training and testing data.

> Features are time_h, offer_id, amount, reward_x ( Will be renamed to ‘reward’), difficulty, duration_h, offer_type, gender, age_group, income_range, member_type

> Target is the event.

## Blog Website <a name="Blog"></a>
A blog has been published  [Analyzing The Starbuck Offers](https://medium.com/@ashwanisng/analyzing-the-starbuck-offers-4189fef3a8cf)
