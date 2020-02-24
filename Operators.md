# Java Operators
Java has a few rules and peculiarities with its operators.  I have noted some of them below for future reference.

## Binary Arithmatic Operators
### Numeric Promotion Rules
1. If two values have different data types, Java will automatically promote one of the values to the larger of the two data types.
2. If one of the values is intergral and the other is floating-point, Java will automatically promote the intergral value to the floating-point value's data type.
3. Data types smaller than an int are promoted to an int any time they are used with a Java binary arithmetic operator.
4. After all promotion has occurred and the operands have the same data type, the resulting value will have the same data type as it promoted operands.

### Examples
- What is the data type of x + y?

      int x = 1; 
      long y = 33;
      ??? = x + y

      Answer: long (Rule #1)

- What is the data type of x + y?

      double x = 39.23;
      float y = 2.1f;
      ??? = x + y

      Answer: double (Rule #1)

- What is the data type of x + y?

      short x = 10;
      short y = 3;
      ??? = x + y

      Answer: int (Rule #3)


## Unary Operators
- A unary operator is one that requires exactly one operand or variable to function.
- Five unary operators are listed below:

      +  = indicates positive number (default)
      -  = indicates a literal negative number or negates an expression
      ++ = Increment value by 1
      -- = Decrement value by 1
      !  = Invert Boolean logical value

## Increment and Decrement Operators
- Two increment and decrement operators are listed below:

      --x = pre-decrement operator
      ++x = pre-increment operator
      x-- = post-decrement operator
      x++ = post-increment operator

- Pre-increment/decrement operators
    - The operator is applied first and the value returned is the new value in the expression.

          int x = 3;
          int y = --x; //

          After running the code above, both x and y have a value of 2.

- Post-increment/decrement operators
    - The original value of the expression is returned, then the operator is applied.

          int x = 3;
          int y = x--;

          After running the code above, x is 2, but y is 3.  The expression, in this case an assignment happens before the post-decrement operator.

- Below is another example of the difference between pre and post decrement/increment operators

      int counter = 0;
      System.out.println(counter);      // Output: 0
      System.out.println(++counter);    // Output: 1
      System.out.println(counter);      // Output: 1
      System.out.println(counter--);    // Output: 1
      System.out.println(counter);      // Output: 0
      System.out.println(counter);      // Output: 0

      The first pre-increment operator updates the value before println is called.  The post-decrement operator updates the counter only after the original value is printed.

- Below is a very obtuse example of multiple pre and post decrement/increment operators on the same line

      int x = 3;
      int y = ++x * 5 / x-- + --x;

      After these two lines have been ran, x is 2 and y is 7.
      
      Moving from left to right, the first pre-increment operator changes x to 4.
      int y = 4 * 5 / x-- + --x;

      Increment/Decrement operators take priority over multiplication and division.  The post-decrement operator changes x to 3, but only after 4 is used in the expression.
      int y = 4 * 5 / 4 + --x; // x is assigned the value of 3

      The last pre-decrement operator is applied before the expression bringing x to 2.
      int y = 4 * 5 / 4 + 2; // x is assigned the value of 2

      Finally order of operations is applied
      int y = 20 / 4 + 2;
      int y = 5 + 2;
      int y = 7;

## Logical Operators
- Three logical operators are listed below:

      & = And
      | = Inclusive Or
      ^ = Exclusive OR

- AND is only true if both operands are true
- Inclusive OR is only false if both operands are false
- Exclusive OR is only true if both operands are different