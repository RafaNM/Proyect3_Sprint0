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
