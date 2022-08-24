# Lecture: Find command

- In this lesson we used the following commands:

Connect to the Atlas cluster:

```bat
mongo "mongodb+srv://<username>:<password>@<cluster>.mongodb.net/admin"
```
```console
show dbs

use sample_training

show collections

db.zips.find({"state": "NY"})
```
- it iterates through the cursor.

```console
db.zips.find({"state": "NY"}).count()

db.zips.find({"state": "NY", "city": "ALBANY"})

db.zips.find({"state": "NY", "city": "ALBANY"}).pretty()

```
                 <!-- Chapter 2 IDE space  -->
Data Explorer Quiz:

In the sample_training.trips collection a person with birth year 1961 took a
trip that started at "Howard St & Centre St". What was the end station name for
that trip?use 
 show dbs
 use sample_training
 show collection
 use trips 
 db.trips.find({"birth":1961, "start station name":"Howard St & Centre St"})


<!-- Find All the Documents Exercise: -->

Using the sample_training.inspections collection find out how many inspections
were conducted on Feb 20 2015.
same as above solution


