# destructuringJavaScript
Destructuring in JavaSript

Destructuring is a huge part of ES6. Along with arrow functions, let, and const, destructuring is probably something we are going to use in every single javascript file in our project.

Consider the case when we fetch object data from API calls, we usually have to write long lines of code to store that data in our files.
If there are 100 lines of data then we write 100 lines of code to extract it and store it. 
ES6 has come up with such a relief of destructuring assignment which allows us to extract even the 100 lines ofdata in just 1 line and yes
that is all. 
Although destructing is huge still I'll cover few of the important ways of using it.
   
                                                    Object Destructuring
                                                    
Basically, you use an object literal on the left-hand-side of an assignment expression for object destructuring.

example 1: Extracting multiple elements of object in a single line.

         const student = {
             name: "Kevin",
             age: 23,
             country: "UK"
             }
             
Older way of extracting the data :

              const name = student.name;
              const age = student.age;
              const country = student.country;
              console.log(`Old method: ${name}, ${age}, ${country}`)
              
ES6 way of extracting the data :
              
               const {name, age, country} = student;  //done!!!!!!
               console.log(`New method: ${name}, ${age}, ${country}`)
               
               
From the above example, Here is an object named student.
A student has name, country and age. 
In the old destructuring method we need to write 3 lines of code to extract all the data but in ES6 we just need only one line. How cool is that !!

                          The same syntax can be used in variable assignment as follows:
                          
                              //Initialize local variable
                                name = 'John';
                                age = 25
                                
                                const student = {
                                        name: "Kevin",
                                        age: 23,
                                        country: "UK"
                                        }  
                           // Reassign firstname and lastname using destructuring
                          // Enclose in a pair of parentheses, since this is an assignment expression
                          
                              ({name, age} = student)
                              console.log(name, age, country); //Kevin 23 UK --> country remains the same
                              
                              
   Note :
Notice that we had to use a pair of enclosing parentheses (()) in the assignment expression. If omitted, the destructuring object literal will be taken to be a block statement, which will lead to an error because a block cannot appear at the left-hand-side of an assignment expression.

ASSIGNMENT OF DIFFERENT VARIABLE NAME:

When we want a different variable name for an object key we only need the colon operator.

 {object_key : new_variable_name } = object_name;
 
 example: 
                        
                         const {name:Name, age: Age, country: Origin} = student;
                         
                         console.log(`${Name} ${Age} ${Origin}) 
                         
                         
ASSIGNMENT OF DEFAULT VARIABLE ::

When we assign a variable corresponding to a key that doesnot exist in the destructing object then it gives undefined. In order to avoid this we can assign a default value to it.
  
                           const {name:Name, age: Age, country: Origin, language = "English"} = student;
                           console.log(`${language}`) //English
                           
                           
NESTED OBJECT DESTRUCTURING

When we have nested objects in the API data we have recieved from the call the in order to extract it in 

example: 
       
                              const nestedObj1 = {
                               name:"kevin",
                               age: 23,
                               country: "Spain",
                               total_marks: {
                                 eng: 90,
                                 hindi:80,
                                 history:70,
                                 maths:60,
                               }
                            }
             
                      const {name, age, country, total_marks : {eng, hindi, history, maths}} = nestedObj1;
                      console.log(`This guy ${name} is a ${age} years old young lad from ${country} has kept ${eng} in english `)
                      
                      
                                                            Array Destructuring
                                      
In array destructuring you can use array literal on left hand side of the asignment expression.
Each variabla name on the array literal maps to corresponding item at the same index on the destructured array.

example:

                                         const rgb = [255, 200, 0];
                                         const [red, green, blue] = rgb;
                                         console.log(`R: ${red} G: ${green} B: ${blue} `)
  
                               Default Values
If the number of items in the array is more than the number of local variables passed to the destructuring array literal, then the excess items are not mapped. But if the number of local variables passed to the destructuring array literal exceed the number of items in the array, then each excess local variable will be assigned a value of undefined except you specify a default value.

example::
          In the following example, we would set default values for some variables in case a corresponding item is not found.
          
                         const rgb = [200]
                         const [red="250", green, blue="0"] = rgb;
                         console.log(`${red} ${green} ${blue}`)   //200 undefined 0
 
 
                 Assignment to variables with array destructuring:
You can also do an array destructuring assignment. Unlike with object destructuring, you don’t need to enclose the assignment expression in parentheses. Here is an example.

                                             let red = 100;
                                             let green = 200;
                                             let blue = 50;

                                             const rgb = [200, 255, 100];

                                             // Destructuring assignment to red and green
                                             [red, green] = rgb;

               console.log(`R: ${red}, G: ${green}, B: ${blue}`); // R: 200, G: 255, B: 50
 
                          SKIPPING ITEMS FROM ASSIGNING LOCAL VARIABLES
                          
  If you dont want certain items to get assigned to local variables then you can separate them via comma separation.
  
  example: 
                              
                               const rgb = [100,288,0]
                               const [,,blue] = rgb;  
                               console.log(`${blue}`);   //0 will be assihned to blue
                               
                               SWAPPING VARIABLES MADE EASY IN ES6
                               
One very nice application of array destructuring is in swapping local variables. Imagine you are building a photo manipulation app and you want to be able to swap the height and width dimensions of a photo when the orientation of the photo is switched between landscape and portrait. The old-fashioned way of doing this will look like the following.

                                      Swapping in old version
                                      
                                   const width = 200;
                                   const height = 100;
                                   let landscape = true
                                   console.log(`${width} x ${height}`);
                                     
                                     if(landscape) {
                                   // adding extra variable for storing the width
                                    const temp1 = width;
                                    //swapping height and width;
                                    width = height;
                                    
                                   // initializing height with the temp variable
                                   height = temp1;
                                   console.log(`${width} x ${height}`);
 
                                             }
                                             
                                  ES6 Version
                                  
                              let width = 200;
                              let height = 300;
                              let landscape= true;
                              if(landscape) {
                               [width, height] = [height, width];
                              }
                             //[300, 200]
                             
                             REST ITEMS
                             
 The new spread operator in es6 can be used with destructuring to achieve this.
 example:: 
 
                     const rainbow = ["violet", "indigo", "blue", green", "yellow", "orange", "red"];
                     
                     //assign violet and indigo only to two different variables and rest to one rest operator
                     
                     const [violet, indigo, ...otherColors] = rainbow;
                     
                     
Note however that the rest items variable, if used, must always appear as the last item in the destructuring array literal otherwise an error will be thrown.

               FANTASTIC ARRAY CLONING::
               
In JavaScript, arrays are reference types and hence they are assigned by reference instead of being copied. So in the following snippet, both the rainbow and the rainbowClone variables point to the same array reference in memory and hence any change made to rainbow is also applied to rainbowClone and vice-versa.

                   Older way of cloning arrays using 
                    1)Array.prototype.slice()
                    2)Array.prototype.concat()
                    
                example::
                
                         const rainbow = ["violet", "indigo", "blue", "green", "yellow", "orange", "red"];
                         
                         // using Array.prototype.slice()
                         
                         const rainbowClone = rainbow.slice() ;  //done
                          rainbow == rainbowClone   //false

                            // using  Array.prototype.concat()
                            const rainbowClone = rainbow.concat()
                            rainbow == rainbowClone   //false
                            
                            
                        CLONING USING ES6 SPREAD OPERATOR::
                        
                    const rainbow = ["violet", "indigo", "blue", "green", "yellow", "orange", "red"];
                    // cloning using spread operator
                    
                     const [...rainbowClone] = rainbow   //YES ITS DONE :)
                    console.log(rainbow === rainbowClone); // false
                    console.log(rainbowClone); // ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet']
                    
               
                         
                       Mixed Destructuring
There are cases when you are working with a pretty complex object/array structure and you need to assign some values from it to local variables. A good example would be an object with several deeply nested objects and arrays. In cases like this, you can use a combination of object destructuring and array destructuring to target certain parts of the complex structure as required. The following code shows a simple example.

example::


                               const items = {
                                  name: "kevin",
                                  age: 90,
                                  location: {
                                      country: States,
                                      coords: [49.08976, 56.90872]
                                      }
                                      }
                                      
                                 //Calling mix of array and object destructing assignments
                                 
                             const {name, age, location: {country, coords :[lat, long]}} = items;
                             console.log(`I am ${name} from ${country}, Latitude(${lat}), Longitude(${lng})`);
                         
                         
                     Destructured Function Parameters
Destructuring can also be applied on function parameters to extract values and assign them to local variables. Note however that the destructured parameter cannot be omitted (it is required) otherwise it throws an error. A good use case is the displaySummary() function from our initial example that expects a student object as parameter. We can destructure the student object and assign the extracted values to local variables of the function. Here is the example again:

              const student = {
                 name: "Kevin",
                 age: 90,
                  scores: {
                     english: 90,
                     hindi:88,
                     maths:10
                     }
                     }
                     
                     function displayName(name,age,scores: {english:0, hindi:0,maths:1}){
                       console.log(`${name} has scored ${english} ${hindi} ${maths} respectively.`);
                       }
                       
Here we extracted the values we need from the student object parameter and assigned them to local variables: name, maths, english and science. Notice that although we have specified default values for some of the variables, if you call the function with no arguments you will get an error because destructured parameters are always required. You can assign a fallback object literal as default value for the student object and the nested scores object in case they are not supplied to avoid the error as shown in the following snippet.

                 function displaySummary({ name, scores: { maths = 0, english = 0, science = 0 } = {} } = {}) {
                   console.log('Hello, ' + name);
                   console.log('Your Maths score is ' + maths);
                   console.log('Your English score is ' + english);
                   console.log('Your Science score is ' + science);
               }

                                       // Calling without a student argument
                                       displaySummary();

                                       // Hello, undefined
                                       // Your Maths score is 0
                                       // Your English score is 0
                                       // Your Science score is 0
                         
                         
                         Happy Reading :)
                         
                         
                         
                         
 Reference: https://medium.com/infancyit/es6-object-destructuring-16b781b034a5
             https://codeburst.io/es6-destructuring-the-complete-guide-7f842d08b98f
