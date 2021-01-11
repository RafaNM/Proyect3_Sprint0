# JavaScript cheat sheet

## Integrate JavaScript to HTML
### <script>...</script>
### <script src="<urlfitxer.js>"></script>

## Comments
### // Line comment's
### /* Block comment's */

## Show and ask for information
### console.log("msg"); ------> Show by console
### document.write("msg");----> Write at doc. HTML
### [window.]alert("msg");----> Show a window
### [window.]prompt("msg");---> Ask for a value
### [window.]confirm("msg");--> Ask for information

## Declaration, assignment and initialization of variables
### var <Variable1Name> [,<Variable2Name>...];
### <VariableName> = <expressio>;
### var <VariableName> = <expressio>;

## Simple variable types
### Strings: doble quotation marks (" ") or simple ones (' ')
### Special characters: \n, \r, \t, \\, \', \", \uNNNN
### <string>.length
### Numeric: entire, real (.), NaN, Infinity
### isNaN (<number>)
### Boolean (true or false)
### Null variable (null)
### Undefined variable (undefined)

## Operators
### Strings concatenation: +
### Assignation ones: = += -=
### Arithmetic ones: + - / * % ++ --
### Logical ones: && || !
### Relational ones: == != < > <= >=
### Types comprovations: tipeof <expressio> number/string/boolean/undefined/object/function
### Conditional operator: (<condicio>)?<valortrue>:<valorfalse>

## Type conversions
### <valor>.toString()
### parseInt(<valor>)
### parseFloat(<valor>)

## Conditional structures
### if (<codition>) {
###  //instructions
### } else if (<codition>) {
###  //instructions
### } else {
###  //instructions
### }

### switch (<codition>) {
###  case <value1>:
###    //instructions ...
###    break;
###  ...
###  default:
###    //instructions ...
### }

### “Falses” Expressions: false,null,undefined,0,NaN,""

## Loops
### while (<codition>) {
###  //instructions
### }

### do {
###  //instructions
### } while (<codition>)

### for (<initialization>; <condition>; <increment>) {
###  //instructions
### }