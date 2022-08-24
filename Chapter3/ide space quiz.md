# Quiz: Updating Documents in the shell

## Problem
Practice Question:

People often confuse NEW YORK City as the capital of New York state, when in
reality the capital of New York state is ALBANY.

In the sample_training.zips collection add a boolean field "capital?" to all
documents pertaining to ALBANY NY, and NEW YORK, NY. The value of the field
should be true for all ALBANY documents and false for all NEW YORK documents.

##Answer 
db.zips.updateMany({"state": "NY", "city":{"$in":["ALBANY","NEW YORK"]}},{"$set":{ "capital?":{"$cond": [ { "$eq": [ "$city", "ALBANY" ] }, true, false ]}}})