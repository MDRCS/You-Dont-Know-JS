# - Getting started with javascript [You-Dont-Know-JS]

- Intro to programming :


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


