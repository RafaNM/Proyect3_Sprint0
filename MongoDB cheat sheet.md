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