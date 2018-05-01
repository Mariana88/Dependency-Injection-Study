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
BEHAVIOR: verifies DOM input for validity (if not empty string) and casts as a Number. Sets the controller object with input numbers. REmpties the DOM input elements

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


---stopped here (below is copy paste from Evan's example)

controller.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: defines the controller object

controller: Object
  PROPERTIES: 2
    view: Object
      INITIALIZED: empty
    model: Object
      INITIALIZED: empty
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
handler.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: defines the handler object

handler: Object
  METHODS: 1
    setup:
      ARGS: 0
      RETURN: undefined
      BEHAVIOR: Sets the controller's 'view' and 'model' properties. 
      	Attaches an event listener to the button under the text box.
```
model.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: defines the model object

model: Object
  PROPERTIES: 1
    text: String
    INITALIZED: empty
  METHODS: 1
    addText: 
      ARGS: 1
        param1: String
        PURPOSE: To be set as this.text
      RETURNS: undefined
      BEHAVIOR: Resets this.string to the parameter value
```
view.js
```
REQUIRES: nothing
EXPORTS: nothing
BEHAVIOR: defines the view object

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
