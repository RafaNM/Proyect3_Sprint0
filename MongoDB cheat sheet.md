# MongoBD cheat sheet

## Finding Documents
### db.ships.findOne() ---------------------------> Finds one arbitrary 
### db.ships.find().prettyPrint() ----------------> Finds all documents and using nice formatting
### db.ships.find({}, {name:true, _id:false}) ----> Shows only the names of the ships 
### db.ships.findOne({'name':'USS Defiant'}) -----> Finds one document by attribute 

## Basic Concepts & Shell Commands
### document db.ships.<command> 
#### db – implicit handle to the used database
#### ships – name of the used collection
### use <database> -------------------------------> Switch to another database
### Show collections -----------------------------> Lists the available collections
### help -----------------------------------------> Prints available commands and help

## Finding Documents using Operators
### $gt / $gte ----------------------------------->Greater than / greater than equals 
### db.ships.find({class:{$gt:’P'} 
### $lt / $lte ----------------------------------->Lesser than / lesser than equals 
### db.ships.find({class:{$lte:’P'}
### $exists -------------------------------------->Does an attribute exist or not
### db.ships.find({type:{$exists:true}})
### $regex --------------------------------------->Perl-style pattern matching 
### db.ships.find({name:{$regex:’^USS\\sE’}}) 
### $type ---------------------------------------->search by type of an element 
### db.ships.find({name : {$type:2}}) 

## BSON Types
### String 2
### Array 4
### Binary Data 5
### Date 9

## Updating Documents
### db.ships.update({name : 'USS Prometheus'}, {name : 'USS Something'}) ----------------------------------> Replaces the whole document
### db.ships.update({name : 'USS Something'}, {$set : {operator : 'Starfleet', class : 'Prometheus'}}) ----> sets / changes certain attributes of a given document
### db.ships.update({name : 'USS Something'}, {$unset : {operator : 1}}) ----------------------------------> removes an attribute from a given document

## Removing Documents
### db.ships.remove({name : 'USS Prometheus'}) ---------> removes the document
### db.ships.remove({name:{$regex:’^USS\\sE’}}) --------> removes using operator

## Working with Indexes
### db.ships.ensureIndex({name : 1}) --------------------------------------------------------> Creating an index
### db.ships.dropIndex({name : 1}) ----------------------------------------------------------> Dropping an index
### db.ships.ensureIndex({name : 1, operator : 1, class : 0}) -------------------------------> Creating a compound index
### db.ships.dropIndex({name : 1, operator : 1, class : 0}) ---------------------------------> Dropping a compound index
### db.ships.ensureIndex({name : 1, operator : 1, class : 0}, {unique : true}) --------------> Creating a unique compound index

## Indexes – Hints & Stats
### db.ships.find ({'name':'USS Defiant'}).explain() ------------> Explains index usage
### db.ships.stats() --------------------------------------------> Index statistics 
### db.ships.totalIndexSize() -----------------------------------> Index size

## Top & Stats System Commands
### ./mongotop ----------------------> Shows time spent per operations per collection
### ./mongostat ---------------------> Shows snapshot on the MongoDB system

## Pipeline Stages
### $project ------------------------------> Change the set of documents by modifying keys and values. This is a 1:1 mapping.
### $match --------------------------------> This is a filtering operation and thus this can reduce the amount of documents that are given as input to the next stage. This can be used for example if aggregation should only happen on a subset of the data.
### $group --------------------------------> This does the actual aggregation and as we are grouping by one or more keys this can have a reducing effect on the amount of documents.
### $sort ---------------------------------> Sorting the documents one way or the other for the next stage. It should be noted that this might use a lot of memory. Thus if possible one should always try to reduce the amount of documents first.
### $skip ---------------------------------> With this it is possible to skip forward in the list of documents for a given amount of documents. This allows for example starting only from the 10th document. Typically this will be used together with “$sort” and especially together with “$limit”.
### $limit --------------------------------> This limits the amount of documents to look at by the given number starting from the current position.
### $unwind -------------------------------> This is used to unwind document that are using arrays. When using an array the data is kind of pre-joined and this operation will be undone with this to have individual documents again. Thus with this stage we will increase the amount of documents for the next stage. 

## Aggregation Examples
### db.ships.aggregate([{$group : {_id : "$operator", num_ships : {$sum : 1}}}]) -------------------------------------------> Counts the number of ships per operator, would be in SQL: SELECT operator, count(*) FROM ships GROUP BY operator;
### db.ships.aggregate([{$project : {_id : 0, operator : {$toLower: "$operator"}, crew : {"$multiply" : ["$crew",10]}}}]) --> Combination of $project-stage and $group-stage.
