# destructuringJavaScript
Destructuring in JavaSript

Destructuring is a huge part of ES6. Along with arrow functions, let, and const, destructuring is probably something we are going to use in every single javascript file in our project.

Consider the case when we fetch object data from API calls, we usually have to write long lines of code to store that data in our files.
If there are 100 lines of data then we write 100 lines of code to extract it and store it. 
ES6 has come up with such a relief of destructuring assignment which allows us to extract even the 100 lines ofdata in just 1 line and yes
that is all. 
Although destructing is huge still I'll cover few of the important ways of using it.

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
                      
  Reference: https://medium.com/infancyit/es6-object-destructuring-16b781b034a5
             https://codeburst.io/es6-destructuring-the-complete-guide-7f842d08b98f
