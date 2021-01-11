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
