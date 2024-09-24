# nosql-challenge
UCI Data Analyst Module 12 - nosql-challenge
Worked with Brendan, Chris, and Wei
Used ChatGPT to Debug code


## Description
I successfully evaluated the food hygiene ratings data from the UK Food Standards Agency. This analysis was done for Eat Safe, Love, a food magazine, to help their journalists and food critics identify key establishments to feature in their future articles.

## Part 1: Database and Jupyter Notebook Set Up
I have already completed the following steps in the NoSQL_setup_starter.ipynb:

Data Import:
Imported the data from the establishments.json file into MongoDB.
Database name: uk_food
Collection name: establishments
Command used for import: mongoimport --db uk_food --collection establishments --file establishments.json --jsonArray

Library Imports:
Imported the required libraries: PyMongo and Pretty Print (pprint).

MongoDB Client Creation:
Created an instance of the MongoDB client to interact with the database.

Database and Data Confirmation:

Listed all databases to confirm uk_food is present.
Confirmed that the establishments collection is in the database.
Retrieved and displayed one document from the establishments collection.
Prepared for Use:
Assigned the establishments collection to a variable for further operations.

## Part 2: Update the Database
I have completed the following modifications to the establishments collection in the uk_food database:

Added a New Halal Restaurant:
A new halal restaurant opened in Greenwich, and it hasn't been rated yet. I added the restaurant to the database.

Retrieved and Updated BusinessTypeID:

Found the BusinessTypeID for "Restaurant/Cafe/Canteen" by querying the database and returning only the BusinessTypeID and BusinessType fields.
Updated the new restaurant with the correct BusinessTypeID based on this query.
Removed Establishments from Dover:

Checked how many documents contained the Dover Local Authority.
Removed all establishments within the Dover Local Authority from the database.
Verified the removal by checking the updated number of documents.
Data Type Corrections:

Used update_many to convert latitude and longitude fields from strings to decimal numbers.
Used update_many to convert RatingValue from a string to an integer.

## Part 3: Exploratory Analysis
I used the NoSQL_analysis_starter.ipynb to answer the specific questions posed by the editors of Eat Safe, Love. Here’s a summary of the tasks completed:

Dataset Exploration Notes:

The RatingValue field ranges from 1-5, where higher values indicate better ratings. Non-numeric values like 'Pass' were coerced to nulls before converting ratings to integers.
Scores for Hygiene, Structural, and ConfidenceInManagement work in reverse; higher scores indicate worse performance in those areas.
Analysis Questions Answered:

Establishments with a Hygiene Score of 20:

Used count_documents to find the number of establishments with a hygiene score of 20.
Displayed the first document using pprint.
Converted the result into a Pandas DataFrame, printed the number of rows, and displayed the first 10 rows.
Establishments in London with a RatingValue ≥ 4:

Used a regular expression ($regex) to search for establishments in the London Local Authority with a RatingValue greater than or equal to 4.
Counted the documents, displayed the first document, and converted the result to a Pandas DataFrame, displaying the top 10 rows.
Top 5 Establishments with a RatingValue of 5 (Nearest to Penang Flavours):

Queried the database for establishments with a RatingValue of 5, sorted by the lowest hygiene score.
Used the geocode to find establishments nearest to "Penang Flavours" (within 0.01 degrees latitude and longitude).
Converted the result to a DataFrame and displayed the first 10 rows.
Local Authorities with the Most Establishments Scoring a Hygiene of 0:

Queried the database to find how many establishments in each Local Authority have a hygiene score of 0.
Sorted the results from highest to lowest, and printed the top ten Local Authority areas.
