# Primitives & Operators

## Objectives

## Introduction

![]()  
—*A blackboard used by Albert Einstein in a 1931 lecture in Oxford. The last three lines give numerical values for the density (ρ), radius (P), and age of the universe. The blackboard is on permanent display in the Museum of the History of Science, Oxford.* ([Wikipedia](https://commons.wikimedia.org/wiki/File:Einstein_blackboard.jpg))


Every commonly-used programming language has the capability to perform simple mathematics. Just like in algebra, numerical values can be saved to variables that can then be used as operands when performing calculations with other values or variables. In Objective-C, these numerical values are called "primitives" and can be of a few different kinds. The four most common primitives you'll see in Objective-C are these:

| Primitive   | Description |
|:-----------:|:------------|
| `NSInteger` | An integer value that can be either positive or negative. |
| `NSUInteger`| An integer value that can **only** be positive (i.e. "unsigned"). |
| `CGFloat`   | A "float" value that can (imperfectly) hold a decimal point. *Do not use float values to hold currency.* |
| `BOOL`      | A `YES` or `NO` value: `0` means "no", `1` means "yes" |


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

We can print primitive values to the console by using the `NSLog()` function, but with specific format specifiers than strings that tell the format string how to translate that primitive's value into a string representation. That string representation is what is then printed to the console allowing us to perceive its value at a given point in the code. Each of these four primitives has its own format specifier listed in the table below:

| Primitive    | Format Specifier |
|:------------:|:----------------:|
| `NSInteger`  | `%li`            |
| `NSUInteger` | `%lu`            |
| `CGFloat`    | `%f` or `%.nf`, *where* `n` *is the number of decimal places to display* |
| `BOOL`       | `%d`             |



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
#### Operators

Just as you would expect, the four mathematical operators can be used to perform simple calculations. The variables or values on either side of the operator are called the "operands", and are the two values with which the calculation will be performed. In Objective-C, the symbols for these operators are:

| Operator | Name | Pronunciation | Description |
|:--------:|:-----|:--------------|:------------|
| `+` | Addition Operator       | "plus" or "add"       | Results to the value that is the **sum** of the two operands. |
| `-` | Subtraction Operator    | "minus" or "subtract" | Results to the **difference** of subtracting the right operand from the left operand.  |
| `*` | Multiplication Operator | "star" or "times"     | Results to the **product** of multiplying the two operands. |
| `/` | Division Operator       | "slash" or "over"     | Results to the **quotient** of dividing the left operand by the right operand. *Integer-only operations will be truncated.* |

```objc
NSInteger a = 1 + 1;
NSInteger b = 2 + 2;
NSInteger c = a + b;
NSInteger d = 30 + a + c - 9;
    
NSLog(@"a: %li, b: %li, c: %li, d: %li", a, b, c, d);
```
This will print:




One per statement:

| Assignment | Name | Pronunciation | Description |
|:----------:|:-----|:--------------|:------------|
| `=`  | Assignment Operator              | "equals" | Assigns the variable to the left of the operator to the final resulting value to the right of the operator. |
| `+=` | Add-and-assignment Operator      | "plus equals" | Assigns the variable to the left of the operator to the **sum** of the final resulting 
| `-=` | Subtract-and-assignment Operator | "minus equals"
| `++` | Increment Operator               | "plus-plus" |
| `--` | Decrement Operator               | "minus-minus" |

| Comparator | Pronunciation | Description |
|:----------:|:--------------|:------------|
| `==` | "is equal to" or "double equals" | Results to `YES` only if the two operands are **exactly equal** in value. |
| `<`  | "less than"                      | Results to `YES` only if the value of the left operand is lower than the value of the right operand. |
| `<=` | "less-than-or-equal-to"          | Results to `YES` if the value of the left operand is lower than or the same as the value of the right operand.
| `>`  | "greater than"                   | Results to `YES` if the value of the left operand is higher than the value of the right operand.
| `>=` | "greater-than-or-equal-to"       | Results to `YES` if the value of the left operand is higher than or the same as the value of the right operand.






| Objective-C Primitive    | C-language Equivalents (do not use these) |
|:------------:|:-----------------------|
| `NSInteger`  | `int`, `long`, `long long` |
| `NSUInteger` | `unsigned int`, `unsigned long`, `unsigned long long` |
| `CGFloat`    | `float`, `double` |
| `BOOL`       | `bool` |






## Primitives

You may have noticed in previous examples that `NSString` variables are declared with a `*` ("star" or "asterisk") while `NSInteger` variables are declared without one. This is because `NSString` is an object type (we'll cover in depth what this means in the next topic). Objects require a pointer reference (the `*`) in their declaration because, well, they point to a set of values at a specific memory address in the computer's RAM. However, `NSInteger` is a primitive, or "data type", and is itself a value, rather than a pointer to a value or set of values.

**Note:** *Entering* `NSInteger *` *will cause the compiler to generate an* `invalid integer to pointer conversion` *warning. The same goes for declaring any of the data types. This syntax does serve a purpose so the language permits it, but your application won't do what you expect.*

The primitives with which you'll interact the most are:

```objc
NSInteger
NSUInteger
CGFloat
BOOL
```
A great reference on the more complete list of primitives can be found in the documentation on Apple's [Foundation Data Types](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Miscellaneous/Foundation_DataTypes/index.html#//apple_ref/doc/c_ref/NSTimeInterval).

### `NSInteger`—neither `int` nor `long`

These Objective-C types get treated at run time as either 32-bit or 64-bit C data types depending on the current device. This is important because the first mobile CPU to run a true 64-bit architecture in a smartphone is the [A7 chip](http://en.wikipedia.org/wiki/Apple_A7) in the iPhone 5S and iPad Mini 3, first released in September 2013.

| Data Type  | Description             | 64-bit            |
|:----------:|:------------------------|:------------------|
|`NSInteger` | `int` (32-bit)          | `long` (64-bit)   |
|`NSUInteger`| `unsigned int` (32-bit) | `unsigned long` (64-bit) |
|`CGFloat`   | `float` (32-bit)        | `double` (64-bit) |
|`BOOL`      | smallest possible unit: | YES = 1, NO = 0 |

### Signed vs. Unsigned Integers

You've probably been wondering what this distinction between signed and unsigned integers means. The most basic explanation is that signed integers can handle values less than zero (negative numbers), while unsigned integers can only be positive. The way signed integers accomplish this is by taking the top half of their available range and using it to count down from -1.

For numbers less than about two billion (2 147 483 647) in Objective-C, incorrectly casting integers to the wrong sign won't cause any problems, but it's good practice to be aware of the distinction. Generally, signed integers should only be used when a value can be below zero, such as a coordinate.

**Advanced:** *Signed integers use their first bit as a* `+` *or* `-` *flag. So on the lower half of the number range, signed and unsigned will convert to the same value. However, an unsigned integer in the top half of the range, if read improperly as a signed integer, will return a negative value. [Further Reading](http://en.wikipedia.org/wiki/Integer_(computer_science))*

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

### Booleans

A **Boolean** (typed `BOOL` in Objective-C) is a true or false (`YES` or `NO`) value. They are most useful in conditional (`if`) statements which we'll cover in the next reading.

You can set a `BOOL` value like this:

```objc
BOOL isYes = YES; // bit value 1, or anything non-zero, or non-"nil"
BOOL isNo = NO; // bit value 0, exactly zero, or "nil"

NSLog(@"yes = %d, no = %d", isYes, isNo);
```
This will print: `yes = 1, no = 0`.

**Top Tip:** *The C language type is* `bool` *(all-lowercase). Use* `BOOL` *(all uppercase) when programming in Objective-C.*
