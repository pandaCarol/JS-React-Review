# web editor
    * [jsbin.com] (http://jsbin.com/?html,output)

# React notes
***
1. what is react：
    * a client-side JS library to built user interfaces
    * The library for web and native user interfaces
    * all about building modern, reactive user interface for the web
    * declarative, component foucused approach

    * react can be used to control ***parts of HTML / widget*** or ***the entrie frontend /SPA*** of web application.
    * means don't actually request from sever, instedad we just used JS through React.js to change what's visible on the screen. That often leads to **a smoother** UI and  a beeter user experience.


2. JS vs react：
    * just with JS an imperative appproach, the code will be very complex
        you have to write every single step that should be taken, 
        like create a element, set its content, add classes, add a click listener...

        * imperative approach: 
            1. we simply describe action after action, step after step
            2. as a developer have to take care about all the nitty-gritty details
            3. have to run the low level code and ***reinvent the wheel*** over and over again, doing repetitive tasks
    * react - code stays maintainable and manageable, do heavy lifting of rendering sth on the screen
        splitting the application into building blocks, small components

3. [Angular Vs React Vs Vue] (https://academind.com/tutorials/angular-vs-react-vs-vue-my-thoughts/)
    * Angular
        * complete component-based UI framework, fouccuses on components just like React
        * it ships more built in feeatures than React
        * it embraces TS right from the start
        * can be overkill for smaller projects since it has way more features built in
    *Vue
        * is kind of like the mixture of Angular and React
        * also complete component-based UI framework, but a bit less features than Angular, but more then React


0. Abbreviation:
| Abbreviation | Contents |
| ------------ | -------- |
| SPA          | Single Page Application | 


# VS Studio - extension
1. extension
    * Prettier - code formatter
    * Material Icon Theme
2. keyboard shortcuts
    * file - preference - keyboard shortcusts (ctrl+K ctrl+S )
    * search **format document**
3. check setting for extension
    * file - preference - keyboard shortcusts (ctrl+, )

# JS Refresher
1. let, const, var
    * let and const are different ways of crating variables.(ES6)
    * use let if you want to create a variable that really is variable
    * use const if you plan on createing a constant value, which you only assign once and never change

    > but then throw an error, since we try to reassign a constant variable which is kind of a strange name

2. JS type: 8 types:
    * 8 data types
        * 7 primitive data type: undefined, null, number, string, boolean, symbol, bigint 
        ```
            const a = null
            console.log(typeof a) // return object

            const b = NaN
            console.log(typof b) // return number
        ```
        * 1 reference data type: object
    * using typeof funciton 
        return 9 results: 
| Type   | Result |
| ------ | ------ |
| Undefined | undefined |
| Null      | object    |
| Boolean   | boolean   |
| Number    | number    |
| BigInt    | bigint    |
| String    | string    |
| Symbol    | symbol    |
| Function  | function  |
| other obj | object    |

    * dynamically-typed languages && weak typing languages
        * belongs to dynamically-typed languages （like python, JS，php）->  checking takes place while the program runs(run-time), no need to specify the data type of each variable while writting code.
    * void 0 -> operator evaluates the given expression and then return undefined;
    * saving space: code space, stack space, heap space



3. [this in JS] (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)
    * ***In most cases, the value of this is determined by how a function is called (runtime binding). It can't be set by assignment during execution,***
    * It can't be set by assignment during execution, and it may be different each time the function is called. 
    * In non–strict mode, this is always a reference to an object. In strict mode, it can be any value. 
    * In non-strict mode, a special process called this substitution ensures that the value of this is always an object. This means:
        * If a function is called with this set to undefined or null, this gets substituted with globalThis.
        * If the function is called with this set to a primitive value, this gets substituted with the primitive value's wrapper object.
    * callback
        * Callbacks are typically called with a this value of undefined (calling it directly without attaching it to any object), which means if the function is non–strict, the value of this is the global object (globalThis).
    * arrow function: 
        * Arrow functions create a closure over the this value of its surrounding scope, which means arrow functions behave as if they are "auto-bound" — no matter how it's invoked, this is set to what it was when the function was created (in the example above, the global object).
    * class context:
        * A class can be split into two contexts: static and instance.
            * Constructors, methods, and instance field initializers (public or private) belong to the instance context.
            *  Static methods, static field initializers, and static initialization blocks belong to the static context.
                * Static methods are not properties of this. They are properties of the class itself. 
                * they are generally accessed on the class, and this is the value of the class (or a subclass).
            * Field initializers are also evaluated in the context of the class.
                * Instance fields are evaluated with this set to the instance being constructed.
                * Static fields are evaluated with this set to the current class.
        * Derived class constructors
            * Derived classes must not return before calling super(), unless the constructor returns an object (so the this value is overridden) or the class has no constructor at all. 
            
4. .bind(), .apply(), .call():
    * The bind() method ***creates a new function*** that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.
    * The call() method ***calls the function*** with a given this value and arguments provided individually.
    * The apply() method calls the specified function with a given this value, and arguments provided as an array (or an array-like object).
        ```
            //
            const array = ['a', 'b'];
            const elements = [0, 1, 2];
            array.push.apply(array, elements);
            console.info(array); // ["a", "b", 0, 1, 2]
        ```
        * The JavaScriptCore engine has **a hard-coded argument limit of 65536**.


5. [regular function vs. arrow function:] (https://dmitripavlutin.com/differences-between-arrow-and-regular-functions/)
    * arrow function do not creat their own this binding: 
        * regular function:
            * this value is dynamic, this depends on how the fun is invoked.
            * There are 4 ways we can invoke a regular fun.
                > Simple invocation:
                ``` 
                    function myFunction() {
                        console.log(this);
                    }
                    myFunction(); // logs global object (window)
                ```
                >Method invocation
                ```
                function myObject() {
                    method() {
                        console.log(this);
                    }
                }
                myObject.method(); // logs myObject
                ```
                >indirect invocation
                ``` 
                    function myFunction() {
                        console.log(this);
                    }
                    const myContext= {value: "A};
                    myFunction.call(myContext); // logs { value: 'A' }
                    myFunction.apply(myContext); //logs { value: 'A' }
                ```
                >constructor invocation
                ``` 
                    function myFunction() {
                        console.log(this);
                    }
                    new myFunction(); // logs an instance of MyFunction
                ```
        * arrow function:
            * this is lexically (it retains the this value of the enclosing lexical context)
            * doesn't define its own execution context but resolves to the one from the outer function
    * Arrow fun cannot be used as constructors: 
        * regular fuc can easily construct objects, but arrow function cannot be used as a constructor.
        ```
            const Car = (color) => {
                this.color = color;
            };
            const redCar = new Car('red'); 
            // TypeError: Car is not a constructor
        ```
    * No arguments object in arrow functions:
        ```
            function myRegularFunction() {
                const myArrowFunction = () => {
                    console.log(arguments);
                }
                myArrowFunction('c', 'd');
            }
            myRegularFunction('a', 'b'); 
            // logs { 0: 'a', 1: 'b', length: 2 }
        ```

        ```
            function myRegularFunction() {
                const myArrowFunction = (...args) => {
                    console.log(args);
                }
                myArrowFunction('c', 'd');
            }
            myRegularFunction('a', 'b'); 
            // logs ['c', 'd']
        ```
        > The arrow function myArrowFunction() is invoked with the arguments 'c', 'd'. Still, inside of its body, arguments object equals the arguments of myRegularFunction() invocation: 'a', 'b'.
        > If you'd like to access the direct arguments of the arrow function, then you can use the rest parameters feature:
    * return:
        * If the return statement is missing, or there's no expression after the return statement, the regular function implicitly returns undefined
        ```
            function myEmptyFunction() {
                42;
            }
            function myEmptyFunction2() {
            42;
            return;
            }
            myEmptyFunction();  // => undefined
            myEmptyFunction2(); // => undefined

            const increment = (num) => num + 1;
            increment(41); // => 42
       ```
    * methods:
    * Arrow functions cannot be declared
        * you need to understand function declaration and function expression.
        * anonymous function 

6. constructor
    ```
    // build a constructor named Person
        function Person(identity) {
            this.identity = identity || 'Person'
        }

    // build instance by using wrapping function
        function _new(Fuc) {
            return function() {
                const obj = {
                    _proto_ = Fuc.prototype
                }

                Fuc.apply(obj, arguments)
                return obj
            }
        }


    // test
        const obj = _new(Person)('son')
        console.log(obj.constructor) // output [function: Person]
        console.log(obj.idetity) // son
    ```

7. class 
    * class can have both proporty and method, and it also supports inheritance 
    * ES6 vs. ES7
        * Properties are like "variable attachted to classes / objects"
            ```
                for ES6:
                constructor() {
                    this.myProperty = "value";
                }

                for ES7:
                myProperty = "value";
            ```
        * Mehtods are like "functions attaced to classes/objects"
            ```
                for ES6: 
                myMethod() {...}

                for ES7
                myMethod = () => {...}
            ```
    ```
        class Cat {
            constructor() {
                this.color = "white";
            }

            printColor() {
                console.log(this.color);
            }
        }

        class Kitty extends Cat {
            constructor() {
                super();
                this.age = "2 months";
            }

            printAge() {
                consolo.log(this.age);
            }
        }

        const kitty = new Kitty();
        consolo.log(kitty.printColor()) // white
        console.log(kitty.printAge())  // 2 months
    ```
    

8. spread & rest operator (...)
    > spread & rest operator => ...
    * Spread: used to split up array ele or object properites
        ```
            const newArray = [...oldArray, 1, 2];
            const newObject = {
                ...oldjObje,
                newProp: 5
            }
        ```
    * rest: used to merge a list of function arguments into an array
        ```
            funciotion sortArgs(...args) {
                return args.sort()
            }

            e.g. 
            const filter = (...args) => {
                return args.filter(el => el === 1);
            }
            console.log(filter(1,2,3));
        ```
