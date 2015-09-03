# Primitives & Operators

## Objectives

## Introduction

![]()  
—*A blackboard used by Albert Einstein in a 1931 lecture in Oxford. The last three lines give numerical values for the density (ρ), radius (P), and age of the universe. The blackboard is on permanent display in the Museum of the History of Science, Oxford.* ([Wikipedia](https://commons.wikimedia.org/wiki/File:Einstein_blackboard.jpg))


Every commonly-used programming language has the capability of performing simple mathematics. Just like in algebra, numerical values can be saved to variables that can then be used as operands when performing calculations with other values or variables. In Objective-C, these numerical values are called "primitives" and can be of a few different kinds. The four most common primitives you'll see in Objective-C are these:

| Primitive   | Description |
|:-----------:|:------------|
| `NSInteger` | An integer value that can be either positive or negative. |
| `NSUInteger`| An integer value that can **only** be positive (i.e. "unsigned"). |
| `CGFloat`   | A "float" value that can (imperfectly) hold a decimal point. **Note:** *Do not use float values to hold currency.* |
| `BOOL`      | A `YES` or `NO` value: `0` means "no", `1` means "yes" |

**Advanced:** *Do not use a* `*` *when declaring primitives. Entering* `NSInteger *` *will cause the compiler to generate an* `invalid integer to pointer conversion` *warning. The same goes for declaring any of the data types. This syntax does serve a purpose so the language permits it, but your application won't do what you expect.*


### Declaring Primitives

The assignment operator (`=`) is used to set a declared variable to an initial value with the following syntax:

```objc
Type name = value;
```
To set a variable of each of these four types to an initial value of zero, we could write them like this: 

```objc
NSInteger i = 0;
NSUInteger u = 0;
CGFloat f = 0.0;
BOOL isFalse = NO;
```

And to set another variable of each of these four types to an initial value of one, we could write them like this:

```objc
NSInteger j = 1;
NSUInteger v = 1;
CGFloat g = 1.0;
BOOL isTrue = YES;
```

### Printing Primitives

We can print primitive values to the console by using the `NSLog()` function, but with specific format specifiers that tell the format string how to translate that primitive's value into a string representation. That string representation is what is then printed to the console allowing us to perceive its value at a given point in the code. Each of these four primitives has its own format specifier listed in the table below:

| Primitive    | Format Specifier |
|:------------:|:----------------:|
| `NSInteger`  | `%li`            |
| `NSUInteger` | `%lu`            |
| `CGFloat`    | `%f` or `%.nf`, *where* `n` *is the number of decimal places to display* |
| `BOOL`       | `%d`             |

To print each of the variables we declared above, we might write a series of `NSLog()`s that looks like this:

```objc
NSLog(@"%li", i);
NSLog(@"%li", j);
NSLog(@"%lu", u);
NSLog(@"%lu", v);
NSLog(@"%f", f);
NSLog(@"%f", g);
NSLog(@"%d", isFalse);
NSLog(@"%d", isTrue);
```
This will print:

```
0
1
0
1
0.000000
1.000000
0
1
```
That's difficult to match up which printout belongs to which variable, though! These format strings work just the same as the ones you've already seen. Let's add some text to each format string to annotate which output belongs to which variable:

```objc
NSLog(@"i: %li", i);
NSLog(@"j: %li", j);
NSLog(@"u: %lu", u);
NSLog(@"v: %lu", v);
NSLog(@"f: %f", f);
NSLog(@"g: %f", g);
NSLog(@"isFalse: %d", isFalse);
NSLog(@"isTrue: %d", isTrue);
```
This will instead print:

```objc
i: 0
j: 1
u: 0
v: 1
f: 0.000000
g: 1.000000
isFalse: 0
isTrue: 1
```
Now are console clearly tells use the value of each variable in our code.

### Reassigning Primitives

Once a primitive has been declared, it can be reassigned in a later statement that uses an assignment operator. The type of the primitive is only used in the declaration, and **not** in reassignments:

```objc
// reassignments

i = 10;
j = -10;
u = 21;
v = 42;
f = 3.1415926536;
g = 1.6180398875;
isFalse = YES;
isTrue = NO;
```
We can then print them a second time to see their new values:

```objc
NSLog(@"i: %li", i);
NSLog(@"j: %li", j);
NSLog(@"u: %lu", u);
NSLog(@"v: %lu", v);
NSLog(@"f: %f", f);
NSLog(@"g: %f", g);
NSLog(@"isFalse: %d", isFalse);
NSLog(@"isTrue: %d", isTrue);
```
This will print: 

```objc
i: 10
j: -10
u: 21
v: 42
f: 3.141593
g: 1.618040
isFalse: 1
isTrue: 0
```

## Operators

### Mathematical Operators

Just as you would expect, the four mathematical operators can be used to perform simple calculations. The variables or values on either side of the operator are called the "operands", and are the two values with which the calculation will be performed. 

**Advanced:** *In addition, the modulus operator can be used to calculate the remainder of clocking the left operand around the right operand. It is included here for completeness.*

In Objective-C, the symbols for these operators are:

| Operator | Name               | Pronunciation | Description |
|:--------:|:-------------------|:--------------|:------------|
| `+` | Addition Operator       | "plus" or "add"       | Results to the value that is the **sum** of the two operands. |
| `-` | Subtraction Operator    | "minus" or "subtract" | Results to the **difference** of subtracting the right operand from the left operand.  |
| `*` | Multiplication Operator | "star" or "times"     | Results to the **product** of multiplying the two operands. |
| `/` | Division Operator       | "slash" or "over"     | Results to the **quotient** of dividing the left operand by the right operand. **Note:** *This operator truncates integer-only divisions.*
 |
| `%` | **Advanced:** Modulus or Modulo       | "modulus" or "modulo" | Results to the **remainder** of clocking the left operand around the right operand. |

We can assign variables to the results of an operation, and we can combine the printouts of a series of variables into a single `NSLog()`:

```objc
NSInteger a = 1 + 1;
NSInteger b = 7 - 2;
NSInteger c = 3 * 4;
NSInteger d = 21 / 3;
NSInteger e = 13 % 7;
    
NSLog(@"a: %li, b: %li, c: %li, d: %li e: %li", a, b, c, d, e);
```
This will print: `a: 2, b: 5, c: 12, d: 7, e: 6`.

```objc
NSInteger ab = a + b;
NSInteger cd = c * d;
    
NSLog(@"ab: %li, cd: %li", ab, cd);
```
This will print: `ab: 7, cd: 60`.

### Increment and Decrement Operators

The increment (`++`) and decrement (`--`) operators are quick ways to "step-up" or "step-down" a variable by one. They are very useful when using an integer variable as a counter.

| Symbol | Name               | Pronunciation | Description |
|:------:|:-------------------|:--------------|:------------|
| `++`   | Increment Operator | "plus-plus"   | Increases the value of the associated variable by `1`.
| `--`   | Decrement Operator | "minus-minus" | Decreases the value of the associated variable by `1`.

Incrementing a variable might look like this:

```objc
NSInteger k = 0;
NSLog(@"k: %li", k);
k++;
NSLog(@"k: %li", k);
k++;
NSLog(@"k: %li", k);
k++;
NSLog(@"k: %li", k);
```
This will print:

```
k: 0
k: 1
k: 2
k: 3
```

Decrementing a variable might look like this:

```objc
NSInteger l = 10;
NSLog(@"l: %li", l);
l--;
NSLog(@"l: %li", l);
l--;
NSLog(@"l: %li", l);
l--;
NSLog(@"l: %li", l);
```
This will print:

```
l: 10
l: 9
l: 8
l: 7
```
Float values can be incremented as well:

```objc
CGFloat m = 1.41421356237;
NSLog(@"m: %f", m);
m++;
NSLog(@"m: %f", m);
m++;
NSLog(@"m: %f", m);
m++;
NSLog(@"m: %f", m);
```
This will print:

```
m: 1.414214
m: 2.414214
m: 3.414214
m: 4.414214
```

### Assignment Operators

In addition to the regular Assignment Operator (`=`), there is an assignment operator related to each of the five mathematical operators in the table above. These other assignment operators *combine* performing a calculation with *and* re-assigning the value of the variable to the left of the operator to the result of the calculation. Only **one** assignment operator should be used per statement:

| Assignment | Name                       | Pronunciation   | Description |
|:----------:|:---------------------------|:----------------|:------------|
| `=`  | Assignment Operator              | "equals"        | Assigns the variable to the left of the operator to the final resulting value to the right of the operator. |
| `+=` | Add-and-assignment Operator      | "plus equals"   | Assigns the variable to the left of the operator to the value of the **sum** of itself plus the value or variable to the right of the operator. | 
| `-=` | Subtract-and-assignment Operator | "minus equals"  | Assigns the variable to the left of the operator to the value of the **difference** between itself and the value or variable to the right of the operator. |
| `*=` | Multiply-and-assignment Operator | "star equals"   | Assigns the variable to the left of the operator to the value of the **product** of multiplying itself with the value or variable to the right of the operator.
| `/=` | Divide-and-assignment Operator   | "slash equals"  | Assigns the variable to the left of the operator to the value of the **quotient** of dividing itself by the value or variable to the right of the operator. **Note:** *This operator truncates integer-only divisions.*
| `%=` | **Advanced:** Remainder-and-assignment Operator| "modulus equals" | Assigns the variable to the left of the operator to the value of the **remainder** of clocking that variable around the value or variable to the right of the operator.

Add-and-assignment operator:

```objc
NSInteger sum = 7;
sum += 6;
NSLog(@"sum: %li", sum);
```
This will print: `sum: 13`.

Subtract-and-assignment operator:

```objc
NSInteger diff = 7;
diff -= 10;
NSLog(@"diff: %li", diff);
```
This will print: `diff: -3`.

Multiply-and-assignment operator:

```objc
NSInteger product = 5;
product *= 3;
NSLog(@"product: %li", product);
```
This will print: `product: 15`.

Divide-and-assignment operator:

```objc
NSInteger quotient = 27;
quotient /= 5;
NSLog(@"quotient: %li", quotient);
```
This will print: `quotient: 5`.

Remainder-and-assignment operator:

```objc
NSInteger remainder = 27;
remainder %= 5;
NSLog(@"remainder: %li", remainder);
```
This will print: `remainder: 2`.

### Comparison Operators

A boolean (`BOOL`) is simply a `YES` or `NO` value. Evaluating booleans is a primary way that programs are structured to make decisions. We'll show you how to apply booleans to decision-making later. For now, just recognize that boolean can be used to capture the result of a comparison between two values or variables. In Objective-C, there are six comparison operators available for use. Some of them should be familiar to you from basic math:

| Comparison | Pronunciation              | Description |
|:----------:|:---------------------------|:------------|
| `==` | "is equal to" or "double equals" | Results to `YES` only if the two operands are **exactly** equal in value. |
| `!=` | "is not equal to"                | Results to `YES` only if the two operands are **not exactly** equal in value.
| `<`  | "less than"                      | Results to `YES` only if the value of the left operand is lower than the value of the right operand. |
| `<=` | "less-than-or-equal-to"          | Results to `YES` if the value of the left operand is lower than or the same as the value of the right operand.
| `>`  | "greater than"                   | Results to `YES` if the value of the left operand is higher than the value of the right operand.
| `>=` | "greater-than-or-equal-to"       | Results to `YES` if the value of the left operand is higher than or the same as the value of the right operand.

```objc
BOOL isEqualTo            = 7 == 7;
BOOL isNotEqualTo         = 7 != 7;
BOOL lessThan             = 5 < 7;
BOOL lessThanOrEqualTo    = 7.0 <= 7;
BOOL greaterThan          = 8 > 7;
BOOL greaterThanOrEqualTo = 7.01 > 7;

NSLog(@"isEqualTo: %d", isEqualTo);
NSLog(@"isNotEqualTo: %d", isNotEqualTo);
NSLog(@"lessThan: %d", lessThan);
NSLog(@"lessThanOrEqualTo: %d", lessThanOrEqualTo);
NSLog(@"greaterThan: %d", greaterThan);
NSLog(@"greaterThanOrEqualTo: %d", greaterThanOrEqualTo);
```
This will print:

```
isEqualTo: 1
isNotEqualTo: 0
lessThan: 1
lessThanOrEqualTo: 1
greaterThan: 1
greaterThanOrEqualTo: 1
```

### Operation Precedence

Operation precedence in Objective-C can affect the expected result of the calculation you intend to make. Just like in algebra, multiplication and division are performed before addition and subtraction unless parentheses are used to override precedence. Because Objective-C uses the C-language operators, operation precedence in Objective-C is similar to [operation precedence in C](https://en.wikipedia.org/wiki/Operators_in_C_and_C%2B%2B).

The precedence of the operators discussed in this reading are in the table below, following **left to right** precedence for operators on the same priority level:

Priority | Operators 
---------|-----------------------------
Highest  | `()` precedence override 
         | `++` `--`
         | `*` `/` `%`
         | `+` `-`
         | `<` `<=` `>` `>=`
         | `==` `!=`
Lowest   | `=` `+=` `-=` `*=` `/=` `%=`

##### Overriding Precedence







### Floating Point Values

In programming, **floating point** values are used to represent decimal values. Objective-C handles floating points with `CGFloat`. If you were to try setting an `NSInteger` to a decimal value, you will lose all of the information following the decimal point.

```objc
NSInteger piInt = 3.14159265359;
NSLog(@"%li", piInt);
```
This will print: `3`.

However, using `CGFloat` to store the value of *pi* will retain the decimal value:

```objc
CGFloat pi = 3.14159265359;
NSLog(@"%f", pi);
```
This will print: `3.141593`.

Notice how it only printed to six decimal places? This has to do with the default setting of the `%f` format specifier, and doesn't reflect the precision of the `CGFloat` value itself. We can override the default length using `%.nf` where `n` is the number of decimal points we wish to see.

```objc
CGFloat pi = 3.14159265359;
NSLog(@"%.12f", pi);
```
This will print: `3.141592653590` since we only set *pi* to the eleventh decimal point.

#### Floating Point Arithmetic

It's important to know that integer values **do not** automatically become floating point values even if you declare the result of a fraction like this:

```objc
CGFloat elevenNinths = 11/9;
NSLog(@"%f", elevenNinths);
```
This will print: `1.000000`.

But why did it not print `1.222222`? Well, that's because dividing (`/`) integer values can only result in another integer. However, if any part of an arithmetic operation involves a floating point value, the result will evaluate to a floating point value as well.

```objc
CGFloat elevenNinths = 11/9.0; // or 11.0/9.0 or 11.0/9
NSLog(@"%f", elevenNinths);
```
This will print: `1.222222`, just like we wanted.


## Avoid the C-language Primitives

Take care to use the Objective-C primitives in favor of the C-language primitives. You may encounter C primitives used in examples online, and occasionally Xcode may even suggest that you use a C primitive. However, **always** convert C primitives to their Objective-C equivalents in your own code.

| C-language Primitives | Use Instead: |
|:---------------------:|:------------:|
| `bool`                | `BOOL`       |
| `double`              | `CGFloat`    |
| `float`               | `CGFloat`    |
| `int`                 | `NSInteger`  |
| `long`                | `NSInteger`  |
| `long long`           | `NSInteger`  |
| `unsigned int`        | `NSUInteger` |
| `unsigned long`       | `NSUInteger` |
| `unsigned long long`  | `NSUInteger` |

**Advanced:** *The reason for this is so your application can dynamically handle being deployed to various device types that have different system architectures. That's a fancy way of saying that some older iPhones have 32-bit processors, while the newer ones have 64-bit processors. Binary word length matters to C primitives, but the Objective-C primitives intelligently chooses the correct binary-word-length C primitive to use.*

