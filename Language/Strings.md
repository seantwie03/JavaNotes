# Strings And StringBuilder
Java has some unique characteristics when dealing with Strings.  In this document I have noted some of the oddities.

- String is uppercase in Java because it is a reference type NOT a primitive type.

## String Pool
- The *String Pool* is a location in the JVM that collects literal Strings.
- Java uses a *String Pool* to alleviate the large amount of memory used by Strings.  Strings are often repeated so collecting them in the String pool, allows the String objects to be reused.
- To allocate a String in the String Pool

      String name = "Fluffy";

- To allocate a String on the Heap

      String name = new String("Fluffy");

## Immutable
- In Java, Strings are immutable.
- The following code creates 27 String objects

      String alpha = "";
      for (char current = 'a'; current <= 'z'; current++) {
          alpha += current;
      }  
      System.out.println(alpha);

    - The empty String is instantiated, then replaced by a new String object each time through the loop.
- To avoid this, StringBuilder is available.

## StringBuilder
- StringBuilder is mutable.
- The following code only creates one StringBuilder object

      StringBuilder alpha = new StringBuilder();
      for (char current = 'a'; current <= 'z'; current++) {
          alpha.append(current);
      }  
      System.out.println(alpha);

    - This code reuses the same StringBuilder

- StringBuilder returns it's reference.

      StringBuilder a = new StringBuilder("one");
      StringBuilder b = a.append("two");

    - After this code is ran, both a and b reference the same StringBuilder object that contains "onetwo"

## Equality
- In Java, string1 == string2 will compare references.

      String z = "Hello World";
      String x = " Hello World".trim();
      System.out.println(z == x); // false

    - Because x is not a literal String, it does not go in the String pool.
    - Because == compares the references
    - The comparison results in false

- Use "str1".equals(str2); when comparing Strings.
    - The String class has a .equals() method that compares the Value rather than the refernce.
    - The StringBuilder does not have this same implementation.
        - .equals() on StringBuilder only compares references (same as ==).