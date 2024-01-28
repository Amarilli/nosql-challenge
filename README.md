# Eat Safe, Love

The UK Food Standards Agency evaluates various establishments across the United Kingdom and gives them a food hygiene rating. The editors of a food magazine, Eat Safe, Love, need to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

## Part 1: Database and Jupyter Notebook Set-Up

I imported the data provided in the `establishments.json` file from my Terminal. I named the database `uk_food` and the collection `establishments`. 

I imported the libraries needed: `PyMongo` and `Pretty Print` (`pprint`).

I created an instance of the Mongo Client.

I assigned the `establishments` collection to a variable to prepare the collection for use.

## Part 2: Update the Database

The magazine editors have some requested modifications for the database before performing any queries or analysis for them. 

An exciting new halal restaurant just opened in Greenwich but hasn't been rated yet. The magazine has asked you to include it in your analysis. 

I found the `BusinessTypeID` for "`Restaurant/Cafe/Canteen`" and I returned only the `BusinessTypeID` and `BusinessType` fields.


The magazine is not interested in any establishments in Dover, so I checked how many documents contain the Dover Local Authority. Then, I removed any 

establishments within the Dover Local Authority from the database, and I checked the number of documents to ensure they were deleted.

Some of the number values are stored as strings, when they should be stored as numbers.

I used `update_many` to convert latitude and longitude to decimal numbers.

I used `update_many` to convert RatingValue to integer numbers.

## Part 3: Exploratory Analysis

Eat Safe, Love has specific questions they want us to answer, which will help them find the locations they wish to visit and avoid.

`RatingValue` refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.

Note: This field also includes non-numeric values such as '`Pass`', where '`Pass`' means that the establishment passed their inspection but isn't given a number 

rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.

The scores for `Hygiene,` `Structural,` and `ConfidenceInManagement` work in reverse. This means the higher the value, the worse the establishment is in these 

areas.

I used `count_documents` to display the number of documents contained in the result.

I displayed the first document in the results using `pprint`.

I converted the result to a Pandas DataFrame, printed the number of rows in the DataFrame, and displayed the first 10 rows.

Then, I answered the following questions:

- Which establishments have a hygiene score equal to 20?

- Which establishments in London have a RatingValue greater than or equal to 4?

- What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

- How many establishments in each Local Authority area have a hygiene score of 0? 



