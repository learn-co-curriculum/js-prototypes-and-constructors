# Objects in JavaScript

Objects in JavaScript generally refer to the `Prototype`/`Instance` object model. These are very similar to other object oriented languages (like Ruby), but the inner mechanics are also fundamentally different.

## Types in JS

Before we get into objects, we need to briefly reiterate the 5 different kinds of non-object types.

There are 5 specific non-object types in Javascript:
    * 3 of the 5 types can be wrapped in object types
        - These are: `boolean`, `number`, and `string`
    * 2 of the 5 types have no specific value
        - These are: `null` and `undefined`
        - `Null` indicates that a variable has been declared, but doesn't have a value
        - `Undefined` indicates that a variable has not been declared in the current scope

## Accessing Properties in JS

There are a couple different ways we can access a property of an object. Instead of explaining them explicitly, I'm just going to list them below:

```javascript
var objWithProps = { color: 'red', name: 'Ian' };

// first method
var objColor = objWithProps.color;
//=> "red"

// second method
var objColor = objWithProps["color"];
//=> "red"
```

## Constructors and Prototypes

In JavaScript, the concept of a `class` doesn't exist like it does in Ruby.

![wat?](http://i0.kym-cdn.com/photos/images/newsfeed/000/173/576/Wat8.jpg?1315930535)

What we do have, though, are JavaScript objects. They consist of a constructor and a prototype.

What is a constructor? A constructor, simply put, is a function that is used as a constructor, meaning that it is a function that will be built upon with additional functionality (through prototypes). The only thing that makes a constructor a constructor function is the fact that the function's name is capitalized. This is a convention for constructors in JavaScript. There's no magic power associated with a function name that's capitalized - it's just simply a convention.

```javascript
function Robot(){
  //...
}

var robot = new Robot();
```

The code above accomplishes three things:

* We've instantiated a new object.
    - `var robot = new Robot();`
* We've set the object `robot` equal to a new instance of the constructor `Robot`.

    ```javascript
    robot.constructor == Robot // true
    robot instanceof Robot // true
    ```

* Finally, the `robot` object will delegate to the `Robot.prototype`.
    - A function is a unique kind of object in Javascript, and has properties. Functions, by default, get a prototype property. It is always an empty hash. A prototype property is empty when a Javascript object is initialized, and you can add properties to the prototype in 2 ways:

    ```javascript
    // prototype property definition - method 1
    Robot.prototype.dance = function(){ console.log("Harder, Better, Faster, Stronger.") }
    ```

    - When an object is constructed (via the `new` keyword), it automatically inherits all of the properties of the object constructor's prototype. 

    ```javascript
    function Monster(){
      //...
    }

    Monster.prototype.swimAbility = 10;
    var kaiju = new Monster();
    kaiju.swimAbility;
    // => 10
    ```
    
    - What does it mean when an object delegates to a prototype for a constructor? It simply just means that, if a property does not yet exist for a specific object `monster`, it will simply give those properties to the object based on how that property is defined on the prototype. So when a `monster` object is instantiated, and a property `swimAbility` doesn't exist yet on instantiation, it will be given that property from `Monster.prototype`.

## Resources

* [Pivotal Labs](http://pivotallabs.com) - [Constructors and Prototypes](http://pivotallabs.com/javascript-constructors-prototypes-and-the-new-keyword/)
