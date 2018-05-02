# DOM-console-node Basic Browser App

## About the app
 Adds two numbers when provided by the user. Can chain additions by remembering the result of a previous addition and adding to it.

A User can:
* enter 2 numbers and view their SUM

Use cases:
* Anything that needs adding (btw, this is an excess of documentation for this project imho)

### Index
* [Use Instructions](#use-instructions)
* [Sourcecode Specs](#sourcecode-specs)
* [Build-Time Diagram](#build-time-diagram)
* [Run-Time Specs](#run-time-specs)
* [Back](./README.md)

---

## Use Instructions

Clone the code to your computer, open 'index.html' with your browser. Enter 2 numbers to be added. For a subsequent time only one number may be entered and the system will add this number to the result of a previous operation.

[TOP](#index)

---


## Sourcecode Specs

index.html
```
REQUIRES: app.js, basic-mvclh-controller.js, basic-browser-handler.js, basic-mvclh-model.js, basic-browser-view.js, basic-mvclh-logic.js
EXPORTS: nothing
BEHAVIOR: none
```
app.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: a) sets controller, model, logic, and view
b) listens to a click on the index.html "addButton" and calls handler upon that click
onbuild: function
	ARGS: 0 (???)
	RETURNS: undefined
	BEHAVIOUR: sets controller, model, logic and view objects. Calls handler.add onclick in DOM object "addButton"
```

basic-browser-handler.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: defines handler object

handler: Object
  PROPERTIES: 1
   controller: object
   	PROPERTIES:0
	METHODS: 0
  METHODS: 1
    add:
      ARGS: 0
      RETURN: undefined
      BEHAVIOR: Gets input elements from the DOM. Verifies input, if empty string stes as undefined, else casts it as Number.
      Calls the controller's add method with input numbers as args. 
      Sets nmber input elements in the DOM to null
```

basic-mvclh-controller.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: a) defines the controller object
b) sets exports in module object as the defined controller

controller: Object
  PROPERTIES: 3
    view: Object
      INITIALIZED: empty
    model: Object
      INITIALIZED: empty
    logic: Object
      INITIALIZED: empty
  METHODS: 1
    add:
      ARGS: 2
        arg1: Number
          PURPOSE: to be passed to logic as input to calculate SUM
	arg2: Number
          PURPOSE: to be passed to logic as input to calculate SUM
      RETURN: undefined
      BEHAVIOR: Retrieves last result from module. Calls logic passing the two input numbers and last result as arguments. Logs the result of the addition(logic) to the console. Calls model to (re)set last result. Calls view to display result.

```

basic-mvclh-model.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: a) defines the model object
b) sets exports in module object as the defined model

model: Object
  PROPERTIES: 1
    lastResult: Number
    INITALIZED: 0
  METHODS: 2
    1)getLastResult: 
      ARGS: none
      RETURNS: undefined
      BEHAVIOR: Retrieves this.lastResult
    2)setLastResult: 
      	ARGS: 1
        	param1: Number
        PURPOSE: To be set as the new "last result" stored
      	RETURNS: undefined
     	BEHAVIOR: Resets this.lastResult to the parameter value
```

basic-mvclh-logic.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: a) defines the logic object
b) sets exports in module object as the defined model

logic: Object
  PROPERTIES: 0
  METHODS: 1
    add: 
      ARGS: 3
      	1) number (a user input number)
	2) number (a second user input number)
	3) number (the last result stored from a previous operation)
      RETURNS: number (the result of the addition operation performed)
      BEHAVIOR: Considers the input provided and decides on which numbers to add: if two numbers provided as user input, adds 	them. If only 1 number provided as user input, adds this number to last result.
```

basic-browser-view.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: a) defines the view object
b) sets exports in module object as the defined view

view: Object
  PROPERTIES: 0
  METHODS: 1
    display: 
      ARGS: 1
        result: Number
        PURPOSE: to be appended into the DOM
      RETURNS: undefined
      BEHAVIOR: Takes in a number and concatenates it 
      		into the innerHTML of the 'output' div
```


[TOP](#index)

---

## Built-Time Diagram

![]()

[TOP](#index)

---

## Run-Time Specs

basic-browser-handler.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: defines handler object

handler: Object
  PROPERTIES: 1
   controller: object
   	PROPERTIES: 3
		view: Object
  			PROPERTIES: 0
 			METHODS: 1
    				display: 
      					ARGS: 1
        					result: Number
        					PURPOSE: to be appended into the DOM
      					RETURNS: undefined
     					BEHAVIOR: Takes in a number and concatenates it into the innerHTML of the 'output' div
    		model: Object
  			PROPERTIES: 1
    				lastResult: Number
    				INITALIZED: 0
  			METHODS: 2
    				1)getLastResult: 
      					ARGS: none
      					RETURNS: undefined
     					BEHAVIOR: Retrieves this.lastResult
    				2)setLastResult: 
      					ARGS: 1
        					param1: Number
        					PURPOSE: To be set as the new "last result" stored
      					RETURNS: undefined
     					BEHAVIOR: Resets this.lastResult to the parameter value
		logic: Object
  			PROPERTIES: 0
  			METHODS: 1
    				add: 
      					ARGS: 3
      						1) number (a user input number)
						2) number (a second user input number)
						3) number (the last result stored from a previous operation)
      					RETURNS: number (the result of the addition operation performed)
      					BEHAVIOR: Considers the input provided and decides on which numbers to add: if two numbers provided as user input, adds them. If only 1 number provided as user input, adds this number to last result.  
				
    	METHODS: 1
    		add:
      			ARGS: 2
        			arg1: Number
          			PURPOSE: to be passed to logic as input to calculate SUM
				arg2: Number
          			PURPOSE: to be passed to logic as input to calculate SUM
     			RETURN: undefined
      			BEHAVIOR: Retrieves last result from module. Calls logic passing the two input numbers and last result as arguments. Logs the result of the addition(logic) to the console. Calls model to (re)set last result. Calls view to display result.

  METHODS: 1
    add:
      ARGS: 0
      RETURN: undefined
      BEHAVIOR: Gets input elements from the DOM. Verifies input, if empty string stes as undefined, else casts it as Number.
      Calls the controller's add method with input numbers as args. 
      Sets nmber input elements in the DOM to null
```

[TOP](#index)

___
___
### <a href="http://elewa.education/blog" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/34921062-506450ae-f97d-11e7-875f-6feeb26ad72d.png" width="100" height="40"/></a>
