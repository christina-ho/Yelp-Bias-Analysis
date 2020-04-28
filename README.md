
##### Contributors to the Project: Ria Pinjani, Tim Zhou, Christina Ho

This is the github repository for the capstone project for the NYU course: *Messy Data and Machine Learning Final Project Fall 2019*.

**## Code File Structure:**
`Scripts` contains code used in this project

 - `Data Cleaning.R` contains code used for reading in large files and initial cleaning
 - `Data Exploration.R`contains code used for exploratory and sentiment analysis
 - `Data Modelling.R` contains code used for modeling, calculating RMSE, and bias

`Data` contains data used in this project

`Paper` contains the final write up with methods and results used for this project

`Figures` contains images and statistical graphs produced

### **Purpose**

Predict bias for Yelp's listed businesses from review text using NLP

### **Approach**
We will look at [Yelp Dataset Challenge’s](https://www.yelp.com/dataset) review dataset to explore if we can detect bias in Yelp reviews.  Yelp’s rating algorithm determines the overall rating without taking into account the reviewers’ special characteristics, while different people may have diverse rating tendency. Some people are reluctant to give a five star while some others  are the opposite. Even when two people have the same view on a restaurant, one may tend to give it a five star while 
the other follow his or her own habit and give three star.

#### Steps
Predict ratings for a unique user-business from review text using NLP
1. Feature Engineering: Create bag of words from the top frequent words in all raw text reviews, or top
frequent words/adjectives from results of Part-of-Speech analysis.


2. Having the bag of words, we treat the problem of predicting a business star as a regression problem.
We will choose four learning models: (i) Multinomial Logistic Regression; (ii) Support Vector Regression; (iii) Support Vector Regression with normalized features; and (iv) Naive Bayes.


3. Look at RMSE as a measure to choose the best model for prediction.


4. Do the prediction and compare the predicted ratings to actual ratings to calculate bias



#### Data Dictionary: Variables description for business.json file
```

{
  // string, 22 character unique string business id
  "business_id": "tnhfDv5Il8EaGSXZGiuQGg",
  
  // string, the business's name
    "name": "Garaje",

    // string, the full address of the business
    "address": "475 3rd St",

    // string, the city
    "city": "San Francisco",

    // string, 2 character state code, if applicable
    "state": "CA",

    // string, the postal code
    "postal code": "94107",

    // float, latitude
    "latitude": 37.7817529521,

    // float, longitude
    "longitude": -122.39612197,

    // float, star rating, rounded to half-stars
    "stars": 4.5,

    // integer, number of reviews
    "review_count": 1198,

    // integer, 0 or 1 for closed or open, respectively
    "is_open": 1,

    // object, business attributes to values. note: some attribute values might be objects
    "attributes": {
        "RestaurantsTakeOut": true,
        "BusinessParking": {
            "garage": false,
            "street": true,
            "validated": false,
            "lot": false,
            "valet": false
        },
    },

    // an array of strings of business categories
    "categories": [
        "Mexican",
        "Burgers",
        "Gastropubs"
    ],

    // an object of key day to value hours, hours are using a 24hr clock
    "hours": {
        "Monday": "10:00-21:00",
        "Tuesday": "10:00-21:00",
        "Friday": "10:00-21:00",
        "Wednesday": "10:00-21:00",
        "Thursday": "10:00-21:00",
        "Sunday": "11:00-18:00",
        "Saturday": "10:00-21:00"
    }
}

```

#### Variables description for user.json file



```
{
    // string, 22 character unique user id, maps to the user in user.json
    "user_id": "Ha3iJu77CxlrFm-vQRs_8g",

    // string, the user's first name
  "name": "Sebastien",
  
  // integer, the number of reviews they've written
    "review_count": 56,

    // string, when the user joined Yelp, formatted like YYYY-MM-DD
    "yelping_since": "2011-01-01",

    // array of strings, an array of the user's friend as user_ids
  "friends": [
    "wqoXYLWmpkEH0YvTmHBsJQ",
    "KUXLLiJGrjtSsapmxmpvTA",
    "6e9rJKQC3n0RSKyHLViL-Q"
    ],
  
  // integer, number of useful votes sent by the user
  "useful": 21,
  
  // integer, number of funny votes sent by the user
  "funny": 88,
  
  // integer, number of cool votes sent by the user
  "cool": 15,
  
  // integer, number of fans the user has
  "fans": 1032,
  
  // array of integers, the years the user was elite
  "elite": [
    2012,
    2013
    ],
  
  // float, average rating of all reviews
  "average_stars": 4.31,
  
  // integer, number of hot compliments received by the user
  "compliment_hot": 339,
  
  // integer, number of more compliments received by the user
  "compliment_more": 668,
  
  // integer, number of profile compliments received by the user
  "compliment_profile": 42,
  
  // integer, number of cute compliments received by the user
  "compliment_cute": 62,
  
  // integer, number of list compliments received by the user
  "compliment_list": 37,
  
  // integer, number of note compliments received by the user
  "compliment_note": 356,
  
  // integer, number of plain compliments received by the user
  "compliment_plain": 68,
  
  // integer, number of cool compliments received by the user
  "compliment_cool": 91,
  
  // integer, number of funny compliments received by the user
  "compliment_funny": 99,
  
  // integer, number of writer compliments received by the user
  "compliment_writer": 95,
  
  // integer, number of photo compliments received by the user
  "compliment_photos": 50
}
```


### Variable desciption for review.json

```

{
  // string, 22 character unique review id
  "review_id": "zdSx_SD6obEhz9VrW9uAWA",
  
  // string, 22 character unique user id, maps to the user in user.json
  "user_id": "Ha3iJu77CxlrFm-vQRs_8g",
  
  // string, 22 character business id, maps to business in business.json
  "business_id": "tnhfDv5Il8EaGSXZGiuQGg",
  
  // integer, star rating
  "stars": 4,
  
  // string, date formatted YYYY-MM-DD
  "date": "2016-03-09",
  
  // string, the review itself
  "text": "Great place to hang out after work: the prices are decent, and the ambience is fun. It's a bit loud, but very lively. The staff is friendly, and the food is good. They have a good selection of drinks.",
  
  // integer, number of useful votes received
  "useful": 0,
  
  // integer, number of funny votes received
  "funny": 0,
  
  // integer, number of cool votes received
  "cool": 0
}

```

