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
      BEHAVIOR: Verifies input, if empty string stes as undefined, else casts it as Number.
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

![](./mvc_list-build-time-diagram.png)

[TOP](#index)

---

## Run-Time Specs

After initialization and durring runtime, the objects being used to run the application are not the same as in the sourcecode.  You can see this with the "Watch" feature in your browser's debugger.  

Eventually you will learn to keep track of this in your mind.  You know you've made it as a programmer when you can track the _state_ of your application as it runs.

```
controller: Object
  PROPERTIES: 2
    view: Object
      PROPERTIES: 0
      METHODS: 1
        display: 
          ARGS: 1
           text: String
           PURPOSE: to be appended into the DOM
        RETURNS: undefined
        BEHAVIOR: Takes in a string and concatenates it 
        		into the innerHTML of the 'printline' div
    model: Object
      PROPERTIES: 1
        text: String
  METHODS: 1
    addText: 
      ARGS: 1
        param1: String
        PURPOSE: To be set as this.text
      RETURNS: undefined
      BEHAVIOR: Resets this.string to the parameter value
    METHODS: 2
      addText:
        ARGS: 1
          param1: String
          PURPOSE: to be added to the model
        RETURN: undefined
        BEHAVIOR: calls this.model.addText() with 'param1' as argument
      print:
        ARGS: 0
        RETURN: undefined
        BEHAVIOR: calls this.view.display() with this.model.text

			        
```

[TOP](#index)

___
___
### <a href="http://elewa.education/blog" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/34921062-506450ae-f97d-11e7-875f-6feeb26ad72d.png" width="100" height="40"/></a>
