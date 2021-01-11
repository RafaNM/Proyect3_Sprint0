# Node.js and Express.js cheat sheet

## The express object. 
### express

## The body-parser object 
### bodyParser

## bodyParser.urlencoded({extended:false})

## The express app object 
### app -------------------------------------------> The app object is the most important object provided by the Express framework
#### app.use
#### app.get
#### app.post
#### app.delete
#### app.put
#### app.listen

## The use method of the app object
### app.use() ------------------------------------> The Express application will invoke the callback function without regard to the path or method (POST or GET) of the incoming request.
### app.use(function(req,res,next){
###     //code goes here
### });

## The GET method of the app object
### app.get() ------------------------------------> The get() method takes a path as an argument, and also a callback function. The callback function provides a request and a response object.
### app.get('/xyz',function(req,res){
###     //code goes here
### });

## The POST method of the app object
### app.post() ----------> Trap and manage an HTTP POST event. Similar to app.get.

## The DELETE method of the app object
### app.delete() --------> Trap and manage an HTTP DELETE event. Similar to app.get.

## The PUT method of the app object
### app.put() -----------> Trap and manage an HTTP PUT event. Similar to app.get.

### The listen method of the app object
### app.listen() ---------> This method defines the port that the express app object will listen on. The callback function executes when the app has been started. The method returns an object that summarizes the properties of the server.
### // here XXXX is the port number
### app.listen(XXXX,function(){});