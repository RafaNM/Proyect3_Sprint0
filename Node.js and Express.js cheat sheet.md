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

## The express request object 
### req -----------> The variable “req” is short for “request”. It represents the data sent to the API endpoint.
### req.query.x 
#### // refers to a query
#### // string parameter x
### req.body.y 
#### // refers to a form tag
#### // with the name of y

## The express response object
### res ----------------------> The variable “res” is short for “response”. It represents the data sent from the API endpoint.
### // The response object will have the following methods:
#### header() 
#### writeHead()
#### write()
#### end()

## The header method of the response object
### res.header() ------------> Sets the response’s HTTP header field to value. Multiple headerkey-value pairs can be written. This method is really just an alias to res.set().

## The writeHead method of the response object
### res.writeHead() ---------> Write the HTTP status code (e.g. 200 = success) and any accompanying HTTP response headers. This method must only be called once on a message and it must be called before response.end() is called.

## The write method of the response object
### res.write() -------------> Write a stream of text to the HTTP response.

## response object
### res.end() ---------------> End the HTTP response.

## The express next object
### next() ------------------> The app callback functions may also provide a next object. When the next() method is called the next matching express app event will be evaluated.