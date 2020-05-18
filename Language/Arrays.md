# Arrays
This section has some information about Arrays in Java.

## Import
- Java arrays require an import statement

      import java.util.*;
      OR
      import java.util.Arrays;

## Declaration
- Declare an Array

      int[] numbers; // Most Common
      int [] numbers1;
      int numbers2[];
      int numbers3 [];

    - Notice how the square brackets can be on the type or the name.  They can also be seperated by a space.
    - The first example is most common.

- Declare an Array with Size

      int[] numbers = new int[3];

    - Initial values will be the default for that type.
      For int the default is 0.

- Declare an Array with Size and Initial Values

      int[] numbers = new int[] {42, 55, 99};

- Declare an Anonymous Array with Size and Initial Values

      int[] numbers = {42, 55, 99}

    - This is called an anonymous array because you don't specify the type on the right side.
    
## Multi-Declaration
- Declare two int Arrays on the same line

      int[] ids, types;

- Declare one int array and one int

      int ids[], types;

    - In this example, ids is an array but types is an int.
    - Just because it is legal doesn't mean it is a good idea.

## Printing Arrays
- Useful method to print arrays

      int[] numbers = {42, 55, 99};
      java.util.Arrays.toString(numbers);

      Output: [42, 55, 99]

## Searching
- Only sorted arrays may be searched.
- Arrays.binarySearch(arrayName, element)
    - If the element is found, the index of the match is returned.
    - If the element is not found, a negative value is returned.  This value is one smaller than the index where a match needs to be inserted to preserve sorted order.
        - For example:

            int[] numbers = {2,4,6,8};
            System.out.println(Arrays.binarySearch(numbers, 2)); // 0
            System.out.println(Arrays.binarySearch(numbers, 3)); // -2

            // 3 is not in the array. The binarySearch method can determine it should be inserted at element 1 to preserve sort order; but, if it returned 1, you would think the element is in the array at index 1.  So it subtracts 1 and negates to get -2.  You may think negation alone would be good enough, since indexes cannot be negative; but, what if an element needs to be inserted at index 0?  Negation alone would return -0.  0 cannot be signed, thus the method subtracts 1 and negates.
      
## Multidimensional Arrays
- Declaration

      int[][] numbers; // Most Common
      int [] numbers1[];

      int [][] numbers = new int[3][2];

- For loop

      int[][] twoD = new int[4][2];
      for (int i = 0; i < twoD.length; i++) {
            for (int j = 0; j < twoD[i].length; j++) {
                  System.out.print(twoD[i][j] + " ");
            }
           System.out.println(); // new row 
      }
      
- Enhanced for loop

      for (int[] inner : twoD) {
            for (int num: inner) {
                  System.out.print(num + " ");
            }
            System.out.println(); // new row
      }