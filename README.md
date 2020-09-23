# - Getting started with javascript [You-Dont-Know-JS]

I- Intro to programming :


        > age = prompt( "Please tell me your age:" );
        > console.log( age );

- Equality :


    == (loose-equals),
    === (strict-equals),
    != (loose not-equals),
    !== (strict not-equals), as in a == b.

1- Strict equality using ===

    Strict equality compares two values for equality. Neither value is implicitly converted to some other value before being compared.

    1-1 If the values have different types, the values are considered unequal.

        Example:
            var num = 0;
            var str_num = new String('0');
            console.log(num === str_num) # false

    1-2 If the values have the same type, are not numbers, and have the same value, they're considered equal.

        Example:
            var num_str_1 = '0';
            var num_str_2 = '0';
            console.log(num_str_1 === num_str_2); # true

    1-3 Finally, if both values are numbers, they're considered equal if they're both not NaN and are the same value, or if one is +0 and one is -0.

        Example:
            var num_1 = 0;
            var num_2 = 0;
            console.log(num_1 === num_2); # true

2- Loose equality using == :

![](./static/loose_equality.png)

    - the loose equality '==' apply a type conversion before comparing as it's expained in the table above.

    var num = 0;
    var obj = new String('0');
    var str = '0';

    console.log(num == num); // true
    console.log(obj == obj); // true
    console.log(str == str); // true

    console.log(num == obj); // true
    console.log(num == str); // true
    console.log(obj == str); // true
    console.log(null == undefined); // true

    // both false, except in rare cases
    console.log(obj == null);
    console.log(obj == undefined);


![](./static/overall_comparaison.png)


- Scope :


    If you ask the phone store employee for a phone model that her store doesn’t carry, she will not be able to sell you the phone you want.
    She only has access to the phones in her store’s inventory. You’ll have to try another store to see if you can find the phone you’re looking for.
    Programming has a term for this concept: scope (technically called lexical scope). In JavaScript, each function gets its own scope.
    Scope is basically a collection of variables as well as the rules for how those variables are accessed by name.
    Only code inside that function can access that function’s scoped variables.

    -> scope is the local variables and other resources that are accessable just though a function :

    Example :

        function one() {
            // this `a` only belongs to the `one()` function vara=1;
            console.log( a );
        }

        function two() {
            // this `a` only belongs to the `two()` function vara=2;
            console.log( a );
        }

        one(); // 1
        two(); // 2


    - Nested scopes :

    function outer() {
        var a=1;

        function inner() {
            var b=2;
            // we can access both `a` and `b` here
            console.log( a + b ); // 3
        }

        inner();
        // we can only access `a` here
        console.log( a ); // 1

    }

    outer();

    -> code inside the innermost scope can access variables from either scope.

    #So, code inside the inner() function has access to both variables a and b, but code only in outer()
     has access only to a—it cannot access b because that variable is only inside inner().

    Recall this code snippet from earlier:
        const TAX_RATE = 0.08;
        function calculateFinalPurchaseAmount(amt) { // calculate the new amount with the tax amt = amt + (amt * TAX_RATE);
                // return the new amount
        return amt;
    }

    The TAX_RATE constant (variable) is accessible from inside the calcu lateFinalPurchaseAmount(..) function,
    even though we didn’t pass it in, because of lexical scope.


II- Into JavaScript :

+ Values & Types :


    --+ JavaScript has typed values, not typed variables. The following built-in types are available:

    • string
    • number
    • boolean
    • null and undefined • object
    • symbol (new to ES6)

    JavaScript provides a typeof operator that can examine a value and
    tell you what type it is:

    var a;
    typeof a; // "undefined"

    a = "hello world";
    typeof a; // "string"

    a=42;
    typeof a; // "number"

    a = true;
    typeof a; // "boolean"

    a = null;
    typeof a; // "object"--weird, bug

    a = undefined;
    typeof a; // "undefined"

    a={b:"c"};
    typeof a; // "object"

    Notice: how in this snippet the a variable holds every different type of value, and that despite appearances,
            typeof a is not asking for the “type of a,” but rather for the “type of the value currently in a.”
            Only values have types in JavaScript; variables are just simple con‐ tainers for those values.

    - Objects
    The object type refers to a compound value where you can set properties (named locations) that each hold their own values of any type.
    This is perhaps one of the most useful value types in all of Java‐ Script:

    varobj={
        a: "hello world",
        b: 42,
        c: true
    };

    obj.a; // "hello world"
    obj.b; // 42
    obj.c; // true

    obj["a"]; // "hello world"
    obj["b"]; // 42
    obj["c"]; // true

    - Keys of objects :

    var obj={
        a: "hello world",
        b: 42
    };

    var b="a";

    obj[b]; // "hello world"
    obj["b"]; // 42

    Arrays
    An array is an object that holds values (of any type) not particularly in named properties/keys, but rather in numerically indexed posi‐ tions. For example:
    vararr=[
        "hello world",
        42,
        true
    ];

    arr[0]; // "hello world"
    arr[1]; // 42
    arr[2]; // true
    arr.length; // 3

    typeof arr; // "object"

    + Arrays vs Objects (usage) :

    The best and most natural approach is to use arrays for numerically positioned values and use objects for named properties.

    + Functions
    The other object subtype you’ll use all over your JS programs is a function:

    function foo() {
        return 42;
    }

    foo.bar = "hello world";
    typeof foo; // "function"
    typeof foo(); // "number"
    typeof foo.bar; // "string"

    + Built-In Type Methods :

    For example:
    var a = "hello world";
    var b = 3.14159;
    a.length; // 11
    a.toUpperCase(); // "HELLO WORLD"
    b.toFixed(4); // "3.1416"

    - Coercion or type conversion :

    Here’s an example of explicit coercion:
    var a = "42";
    var b=Number(a);
    a; // "42"
    b; // 42--the number!
    And here’s an example of implicit coercion:
    var a = "42";
    var b = a * 1; // "42" implicitly coerced to 42 here
    a; // "42"
    b; // 42--the number!


    - Strict Mode :

    You can use strict mode in all your programs. It helps you to write cleaner code, like preventing you from using undeclared variables.

    - Examples :

        "use strict";
        x = 3.14;       // This will cause an error because x is not declared

        ------------------------------------------------------------------------------

        "use strict";
        myFunction();

        function myFunction() {
          y = 3.14;   // This will also cause an error because y is not declared
        }

        ------------------------------------------------------------------------------

        x = 3.14;       // This will not cause an error.
        myFunction();

        function myFunction() {
          "use strict";
          y = 3.14;   // This will cause an error
        }

