# Backend - Database - Basics - Let's MonGO

## Let's monGO

Add your answers directly into this README file.

1. Explain ObjectIDs in MongoDB; what are they?

ANSWER 
------ 
 MongoDB uses ObjectIds as the default value of _id field of each document (object), which is generated while the creation of any document. The complex combination of ObjectId makes all the _id fields unique.
 ObjectIds are small, likely unique, fast to generate, and ordered. ObjectId values are 12 bytes in length, consisting of:

a 4-byte timestamp value, representing the ObjectId's creation, measured in seconds since the Unix epoch
a 5-byte random value
a 3-byte incrementing counter, initialized to a random value.



2. You have a collection called "users" with a document like this: `{ _id: 1, name: "Veera" }`. What query would you use to update the name to "Princess Veera Silkenfur"?

ANSWER 
------ 
db.users.updateOne({ _id: 1, }, {$set: { "name": "Princess Veera Silkenfur" }});



3. How do you make a collection?

ANSWER 
------ 
db.createCollection("newCollection");
**or**
db.newCollection.insertOne({ _id: 1, name: "Pipa", age: 35 });


4. So the (old) mongo shell is kind of like a JavaScript REPL. What is a REPL? 
Which other REPL have we used?

ANSWER 
------ 
What is a REPL? 
REPL (READ, EVAL, PRINT, LOOP) is a computer environment similar to Shell (Unix/Linux) and command prompt. ... System interacts with the user through outputs of commands/expressions used. It is useful in writing and debugging the codes.
Typical functionality provided by a Lisp REPL includes:
    
    * History of inputs and outputs. 
    * Variables are set for the input expressions and results. These variables are also available in the REPL. For example in Common Lisp * refers to the last result, ** and *** to the results before that.
    * Levels of REPLs. In many Lisp systems if an error occurs during the reading,  evaluation or printing of an expression, the system is not thrown back to the top-level with an error message. Instead a new REPL, one level deeper, is started in the error context. The user can then inspect the problem, fix it and continue – if possible. If an error occurs in such a debug REPL, another REPL, again a level deeper, is started. Often the REPL offers special debug commands.
    * Error handling. The REPL provides restarts. These restarts can be used, when an error occurs, to go back to a certain REPL level.
    * Mouse sensitive input and output of data objects.
    * Input editing and context specific completion over symbols, pathnames, class names and other objects.
    * Help and documentation for commands.
    * Variables to control the reader. For example, the variable *read-base* controls in which base numbers are read by default.
    * Variables to control the printer. Example: maximum length or maximum depth of expressions to print.
    * Additional command syntax. Some REPLs have commands that follow not the s-expression syntax, but often work with Lisp data as arguments.
    * Graphical REPLs. Some Lisp REPLs (the CLIM Listener is an example) accept also graphical input and output.


Which other REPL have we used?
REPL JS (javascript) and  REPL in Node.js


5. So the (old) mongo shell is kind of like a JavaScript REPL. You can use things like variables, try...catch  statements and loops. Experiment with it and find at least three other JavaScript things that we have used that work in the (old) shell. If you can, try to find even more!

ANSWER 
------ 
You can assign a value to the variable.

           >>    print("something");    
                    prints --->  something

           >>    let firstString = "Hello";     

           >>    let newString = firstString + " World. Hola, Hola!";
           >>    newString
                    prints --->  Hello World. Hola, Hola!

           >>   let arrayNum = ["one", "two", "three"];
           >>   let first = arrayNum[0];
           >>   first;
                   prints ---> One
 
Outputting Data           
           >>    let cat= db.users.findOne();
           >>    cat
                    prints --->  { "_id" : 1, "name" : "Princess Veera Silkenfur" }


          >>    print(cat.name);  
                    prints ---> Princess Veera Silkenfur

          >>    printjson(cat);
                    prints --->  { "_id" : 1, "name" : "Princess Veera Silkenfur" }
                    *( this method prints a pretty form of the JavaScript object.)
          >>    print(JSON.stringify(cat));
                    prints --->  {"_id":1,"name":"Princess Veera Silkenfur"}
                    *(prints a tightly compact string form of a JavaScript object.)

Arithmetic Operators
  = , + ,  - , * , / , % , ++ , --

         > x = 5;
           5
         > y = 6;
           6
         > x + y;
           11
         > x * y
           30
         > y++
           6
         > x--
           5
        > x--
           4
        > x--
           3
        > y++
           7
        > y++
           8
        > 11 / x
           5.5
        > y%2
           1

Assignment Operators

        > x = 7
           7
        > x+=7
          14
        > x-=7
          7
        > x*=7
          49
        > x%=7
          0
        > x/=7
          0
        > x=7
          7
        > x/= 7
          1

 Comparison Operators
          > x = 5
            5
          > x==7
            false
          > x==5
            true
          > x===5
            true
          > x==="5"
            false
          > x!=5
             false
          > x!=="5"
             true
          > x>3
             true
          > x<10
             true
          > x<=5
             true

          > x = 6
            6
          > y = 4
            4
          > (x==6 && y==4)
            true
          > (x==6 && y>x)
            false
          > (x>=6 || y>x)
            true

if Statements 
             
          >>  if(x<5){
                do_something();
              } else if(x<10) {
                do_something_else();
              } else {
                do_nothing();
              }

           >>    x = 7;
           >> if(x<5){
                x++;
              } else if(x>10) {
                x--;
              } else {
                null;
              }
                 ---> prints null

for loops & for in loops
            >> for (let x=1; x<=3; x++){
                 for (let y=1; y<=3; y++){
                   print(x + " X " + y + " = " + (x*y) + "\n");
                 }
               } 
                 ----> prints 1 X 1 = 1

                              1 X 2 = 2
                              
                              1 X 3 = 3
                              
                              2 X 1 = 2
                              
                              2 X 2 = 4
                              
                              2 X 3 = 6
                              
                              3 X 1 = 3
                              
                              3 X 2 = 6
                              
                              3 X 3 = 9


              >> let week = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
              >>  for (let day in week){
                  print("It's " + week[day] + "\n");
                }  
                ---> it prints It's Monday

                               It's Tuesday
                               
                               It's Wednesday
                               
                               It's Thursday
                               
                               It's Friday
                               
                               It's Saturday
                               
                               It's Sunday
                               

 Passing variables aas functions

                >> let firstName = "Maria"
                >> function greeting(firstName, city) {   
                    print("Hello " + firstName);   
                    print(". How is the weather in " + city); }
                >> greeting(firstName, "Berlin");
                    ----> it prints  
                    Hello Maria
                    . How is the weather in Berlin

                >>  function formatGreeting(name, city) { 
                    let retStr = "";
                    retStr += "Hello " + name + "\n";
                    retStr += "Best painter of " + country + "!";
                    return retStr;
                    }
                    let greet = formatGreeting("Frida Kahlo", "Mexico");
                    print(greet);

                       ---> it prints Hello Frida Kahlo
                                    Best painter of Mexico!

 Object Syntax
               >> let user = new Object();
               >> user.first="Rita";
               >> user.last="Payés";
               >> user.getName = function( ) { 
                   return this.first + " " + this.last; }                                   


map 

>> we can check all collections and its documents with map for example

           >> db.getCollectionNames().map( (name) => ({[name]: db[name].find().toArray().length}) )
               
               ---> it prints alphabetically
                       [
                        	{
                        		"cats" : 3
                        	},
                        	{
                        		"foods" : 1
                        	},
                        	{
                        		"inventory" : 3
                        	},
                        	{
                        		"products" : 2
                        	},
                        	{
                        		"users" : 1
                        	}
                        ]
forEach 

                    > use gameOfThrones
 
                    > db.editors.insertMany( [
                        { "_id" : "101", "full_name" : "Daniel Atlas" }, 
                        { "_id" : "102", "full_name" : "Charlotte Neil" },
                        { "_id" : "103", "full_name" : "James Breen" },
                        { "_id" : "104", "full_name" : "John Gordon" },
                        { "_id" : "105", "full_name" : "Rick Ford" },
                        { "_id" : "106", "full_name" : "Susan Dixit" },
                        { "_id" : "107", "full_name" : "John Snow" },
                        { "_id" : "108", "full_name" : "Arya Stark" },
                        { "_id" : "109", "full_name" : 25 },
                        { "_id" : "110", "full_name" : "John Daniel" }
                    ] )

                    >> db.editors.find().pretty()
                      ---> it prints
                         { "_id" : "101", "full_name" : "Daniel Atlas" }
                         { "_id" : "102", "full_name" : "Charlotte Neil" }
                         { "_id" : "103", "full_name" : "James Breen" }
                         { "_id" : "104", "full_name" : "John Gordon" }
                         { "_id" : "105", "full_name" : "Rick Ford" }
                         { "_id" : "106", "full_name" : "Susan Dixit" }
                         { "_id" : "107", "full_name" : "John Snow" }
                         { "_id" : "108", "full_name" : "Arya Stark" }
                         { "_id" : "109", "full_name" : 25 }
                         { "_id" : "110", "full_name" : "John Daniel" }

                    >> db.editors.find().forEach( function(myDoc) { print( "User: " + myDoc.full_name ); } )
                          ---> it prints
                          User: Daniel Atlas
                          User: Charlotte Neil
                          User: James Breen
                          User: John Gordon
                          User: Rick Ford
                          User: Susan Dixit
                          User: John Snow
                          User: Arya Stark
                          User: 25
                          User: John Daniel
                          
  >>adds a new editor Susan Powell

                    >> db.editors.find( { full_name: 25 } ).forEach(function(doc) {    
                        var updated_name = "Susan Powell";
                        db.editors.update( { _id: doc._id }, { $set: { "full_name": updated_name } } );
                    }) 
                        ---> it prints
                        User: Daniel Atlas
                        User: Charlotte Neil
                        User: James Breen
                        User: John Gordon
                        User: Rick Ford
                        User: Susan Dixit
                        User: John Snow
                        User: Arya Stark
                        User: Susan Powell
                        User: John Daniel


>> delete the new editor

                    >> db.editors.find( { full_name: "Susan Powell" } ).forEach(function(doc){
                    db.editors.remove( { _id: doc._id } );
                    })

6. (Research) So the old shell is pretty cool. How is the new shell better?

ANSWER 
------
The new MongoDB Shell, mongosh , offers numerous advantages over the legacy mongo shell, such as: Improved syntax highlighting. Improved command history. Improved logging. Mongosh currently supports a subset of the legacy mongo shell methods. To maintain backwards compatibility, the methods that the new mongosh supports use the same syntax as the corresponding methods in the legacy mongo shell.


7. (Research) How can you insert multiple documents at the same time?

ANSWER 
------    
    with db.collection.insertMany() . Example follows.

            >>  db.inventory.insertMany([
              { item: "Jackets", qty: 25, tags: ["blank", "red"], size: { xs: 14, s: 21, m: 43, l: 21 } },
              { item: "Trousers", qty: 85, tags: ["gray"], size: { xs: 6, s: 24, m: 46, l: 7 } },
              { item: "Shirts", qty: 25, tags: ["cyan", "blue"], size: { xs: 34, s: 34, m: 6, l: 35 } }
           ])

           >> db.inventory.find( {} )

                 ---> it prints 
                 { "_id" : ObjectId("61433b6eab8917c5dd10841c"), "item" : "Jackets", "qty" : 25, "tags" : [ "blank", "red" ], "size" : { "xs" : 14, "s" : 21, "m" : 43, "l" : 21 } }
                 { "_id" : ObjectId("61433b6eab8917c5dd10841d"), "item" : "Trousers", "qty" : 85, "tags" : [ "gray" ], "size" : { "xs" : 6, "s" : 24, "m" : 46, "l" : 7 } }
                 { "_id" : ObjectId("61433b6eab8917c5dd10841e"), "item" : "Shirts", "qty" : 25, "tags" : [ "cyan", "blue" ], "size" : { "xs" : 34, "s" : 34, "m" : 6, "l" : 35 } }


8. (Research) You have a collection called `cats` with a documents like this: `{ name: "Veera" }, { name: "Rauli" }, { name: "BenBen" }` - How can you insert the field `cute: true` into all of them with one command?


ANSWER 
------

 >> we have a collection called cats
            
             >> db.cats.insertMany([{ name: "Veera" }, { name: "Rauli" }, { name: "BenBen" }]);
    
    
>> insert cute field in all documents of cats collection
           
            >> db.cats.update({},
                 {$set : {cute: "cute"}},
                 {upsert : false,
                 multi : true})  

                 ---> it prints  WriteResult({ "nMatched" : 3, "nUpserted" : 0, "nModified" : 3 })


>> we can check it with a pretty print

            >> db.cats.find().pretty()

              ---> it prints
                {
                	"_id" : ObjectId("61433e74ab8917c5dd108420"),
                	"name" : "Veera",
                	"cute" : "cute"
                }
                {
                	"_id" : ObjectId("61433e74ab8917c5dd108421"),
                	"name" : "Rauli",
                	"cute" : "cute"
                }
                {
                	"_id" : ObjectId("61433e74ab8917c5dd108422"),
                	"name" : "BenBen",
                	"cute" : "cute"
                }
              



9. (Task) Start a timer for 30 minutes. Spend all that time getting to know and reading https://docs.mongodb.com/manual/introduction/ - how far did you get? What was the most cool or interesting thing you learned?
I got to the Time Series Collections but I found out I couldn't test some stuff since it has been deprecated or only available to the new shell version (cursor.hint(), etc..). I wonder if it just makes sense to install mongosh and be more up to date to test the features.
The pipeline construction and follow up of collection, I need to test that, reading the documentation is not enough, but it seems pretty interesting with things like $match, $group, $merge state. CApped collections seems to be interesting if you have a high volume of documents with a max. and the last one overwrites older ones.
I love the commands find() and find().pretty() sort() etc to check the collections. I have learned to map through them, etc...
First time I heard about the BSON. MongoDB stores data records as BSON documents. BSON is a binary representation of JSON documents, though it contains more data types than JSON.
But basically I nned to test much more stuff to see if and how does it work...


10. Find one SQL Cheatsheet and one MongoDB Cheatsheet and add links to them here.


 link to a 3 page  SQL Cheatsheet pdf file
    https://www.sqltutorial.org/wp-content/uploads/2016/04/SQL-cheat-sheet.pdf


 link to MongoDB cheatsheet 
    https://www.mongodb.com/developer/quickstart/cheat-sheet/   































🌿
