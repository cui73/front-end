# ES6 new features

## ES6 New Features

* **Let, Const**
* **Class**
* **Arrow Function**
* **Spread Operator** **and Destructing**
* **Modules**
* **Promise**
* **Symbol**
* Typed Arrays
* Internationalization & Localization



## Class

```javascript
// ES6
class Human {
    constructor() {
        this.gender = "female";
    }
    
    printGender() {
        console.log(this.gender);
    }
}

class Person extends Human {
    constructor() {
        super();
        this.name = "Harry";
        this.gender = "male";
    }
    
    printMyName() {
        console.log(this.name);
    }
}

const person = new Person();
person.printMyName(); // "Harry"
person.printGender(); // "male"

// ES7
class Human {            
    gender = "female";           
    
    printGender = () => {        
        console.log(this.gender);    
    }
}

class Person extends Human {           
    name = "Harry";        
    gender = "male";         
    
    printMyName = () => {        
        console.log(this.name);    
    }
}
const person = new Person();
person.printMyName(); // "Harry"
person.printGender(); // "male"
```

## Exports & Imports

| Default export | Named export |
| :--- | :--- |
| You can choose the name when import | Name is defined by export |
| `import person from "./person.js"` | `import {person as Person} from "./utility.js"` |
|  | `import * as bundle from "./utility.js"` |

## Spread & Rest Operators `...`

| Spread | Rest |
| :--- | :--- |
| Used to split up array elements OR object properties | Used to merge a list of function arguments into an array |
| `const newObject = {...oldObject, newProp: 5};` | `function sortArgs(...) {return args.sort();}` |

## Destructuring

Easily extract array elements or object properties and store them in variables

| Array Destructuring | Object Destructuring |
| :--- | :--- |
| `[a, b] = ["Hello", "Harry"];` | `{name} = {name: "Harry", gender: "male"};` |

## Declaration

[`let`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)Declares a block-scoped, local variable, optionally initializing it to a value.

[`const`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)Declares a block-scoped, read-only named constant.

[`var`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)Declares a variable, optionally initializing it to a value.

