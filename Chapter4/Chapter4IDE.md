# Chapter 4 IDE

## Problem:
- In this IDE space you can find two pre-populated text files:

- Contains all examples that were used in the lessons in this chapter.
Contains all the questions that you encountered in labs and quizzes throughout the chapter.
Use this space to:

- connect to your Atlas cluster,
- practice what you learned in earlier lectures,
- find answers to the quiz questions in this chapter.
Remember, it is easier to view documents in the shell when they look pretty()

_Good luck!_

- If you want to install MongoDB on your computer and use it locally instead of using this IDE environment consult our documentation for installation instructions for your specific Operating System. We will not be providing support for local installations in this course.

**Hint: If you are consistently getting the wrong answer but you are confident in your solution you may have modified the dataset and the modifications cause an incorrect result. Solution: Delete the sample dataset then load a fresh one to complete the exercise. Be mindful of dataset changes as you are working on assignments in this course.**

## Answer
Connect to Atlas Cluster
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"

use sample_training
Find all documents where the tripduration was less than or equal to 70 seconds and the usertype was not Subscriber:
db.trips.find({ "tripduration": { "$lte" : 70 },
                "usertype": { "$ne": "Subscriber" } }).pretty()
            Find all documents where the tripduration was less than or equal to 70 seconds and the usertype was Customer using a redundant equality operator:
db.trips.find({ "tripduration": { "$lte" : 70 },
                "usertype": { "$eq": "Customer" }}).pretty()
Find all documents where the tripduration was less than or equal to 70 seconds and the usertype was Customer using the implicit equality operator:
db.trips.find({ "tripduration": { "$lte" : 70 },
                "usertype": "Customer" }).pretty()

      Find all documents where airplanes CR2 or A81 left or landed in the KZN airport:
db.routes.find({ "$and": [ { "$or" :[ { "dst_airport": "KZN" },
                                    { "src_airport": "KZN" }
                                  ] },
                          { "$or" :[ { "airplane": "CR2" },
                                     { "airplane": "A81" } ] }
                         ]}).pretty()

     <!-- Find all documents where the trip started and ended at the same station: -->
db.trips.find({ "$expr": { "$eq": [ "$end station id", "$start station id"] }
               }).count()
<!-- Find all documents where the trip lasted longer than 1200 seconds, and started and ended at the same station: --> -->
db.trips.find({ "$expr": { "$and": [ { "$gt": [ "$tripduration", 1200 ]},
                         { "$eq": [ "$end station id", "$start station id" ]}
                       ]}}).count()

<!-- Find all documents with exactly 20 amenities which include all the amenities listed in the query array: -->
db.listingsAndReviews.find({ "amenities": {
                                  "$size": 20,
                                  "$all": [ "Internet", "Wifi",  "Kitchen",
                                           "Heating", "Family/kid friendly",
                                           "Washer", "Dryer", "Essentials",
                                           "Shampoo", "Hangers",
                                           "Hair dryer", "Iron",
                                           "Laptop friendly workspace" ]
                                         }
                
                
                use sample_training

db.trips.findOne({ "start station location.type": "Point" })

db.companies.find({ "relationships.0.person.last_name": "Zuckerberg" },
                  { "name": 1 }).pretty()

db.companies.find({ "relationships.0.person.first_name": "Mark",
                    "relationships.0.title": { "$regex": "CEO" } },
                  { "name": 1 }).count()


db.companies.find({ "relationships.0.person.first_name": "Mark",
                    "relationships.0.title": {"$regex": "CEO" } },
                  { "name": 1 }).pretty()

db.companies.find({ "relationships":
                      { "$elemMatch": { "is_past": true,
                                        "person.first_name": "Mark" } } },
                  { "name": 1 }).pretty()

db.companies.find({ "relationships":
                      { "$elemMatch": { "is_past": true,
                                        "person.first_name": "Mark" } } },
                  { "name": 1 }).count()