
## 1. Write a program to find the factorial of a number.
```java
import java.util.Scanner;

public class Factorial {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a non-negative integer: ");
        
        int number = scanner.nextInt();
        scanner.close();

        long factorial = calculateFactorial(number);
        
        if (factorial == -1) {
            System.out.println("Factorial is not defined for negative numbers.");
        } else {
            System.out.println("Factorial of " + number + " is: " + factorial);
        }
    }

    public static long calculateFactorial(int n) {
        if (n < 0) {
            return -1; // Factorial is not defined for negative numbers
        }

        long result = 1;
        for (int i = 2; i <= n; i++) {
            result *= i;
        }

        return result;
    }
}
```
## 2. Implement a program to check if a number is prime.

```java
import java.util.Scanner;

public class PrimeChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a positive integer: ");
        
        int number = scanner.nextInt();
        scanner.close();

        boolean isPrime = isPrimeNumber(number);
        
        if (isPrime) {
            System.out.println(number + " is a prime number.");
        } else {
            System.out.println(number + " is not a prime number.");
        }
    }

    public static boolean isPrimeNumber(int n) {
        if (n <= 1) {
            return false; // 1 and non-positive numbers are not prime
        }

        if (n <= 3) {
            return true; // 2 and 3 are prime
        }

        if (n % 2 == 0 || n % 3 == 0) {
            return false; // Multiples of 2 or 3 are not prime
        }

        for (int i = 5; i * i <= n; i += 6) {
            if (n % i == 0 || n % (i + 2) == 0) {
                return false; // Check for factors in the form 6k +/- 1
            }
        }

        return true;
    }
}
```
## 3. Create a program to reverse a string.
```java
public class StringReversal {
    public static void main(String[] args) {
        // Input string
        String input = "Hello, World!";
        
        // Call the reverseString method
        String reversed = reverseString(input);
        
        // Display the reversed string
        System.out.println("Original string: " + input);
        System.out.println("Reversed string: " + reversed);
    }
    
    public static String reverseString(String input) {
        // Convert the string to a character array
        char[] charArray = input.toCharArray();
        
        // Initialize pointers for reversing
        int left = 0;
        int right = charArray.length - 1;
        
        // Reverse the string using a two-pointer approach
        while (left < right) {
            // Swap characters at left and right pointers
            char temp = charArray[left];
            charArray[left] = charArray[right];
            charArray[right] = temp;
            
            // Move the pointers towards the center
            left++;
            right--;
        }
        
        // Convert the character array back to a string
        String reversed = new String(charArray);
        
        return reversed;
    }
}
```
## 4. Write a Java program to swap two numbers without using a temporary variable.

```java
public class SwapNumbersWithoutTemp {
    public static void main(String[] args) {
        int num1 = 5;
        int num2 = 10;
        
        System.out.println("Before swapping:");
        System.out.println("num1 = " + num1);
        System.out.println("num2 = " + num2);
        
        // Swap the numbers without a temporary variable
        num1 = num1 + num2;
        num2 = num1 - num2;
        num1 = num1 - num2;
        
        System.out.println("After swapping:");
        System.out.println("num1 = " + num1);
        System.out.println("num2 = " + num2);
    }
}
```
## 5. Implement a program to check if a string is a palindrome.

```java
public class PalindromeChecker {
    public static void main(String[] args) {
        String input = "racecar"; // Change this to the string you want to check

        if (isPalindrome(input)) {
            System.out.println(input + " is a palindrome.");
        } else {
            System.out.println(input + " is not a palindrome.");
        }
    }

    public static boolean isPalindrome(String str) {
        // Remove spaces and convert to lowercase for case-insensitive comparison
        str = str.replaceAll("\\s", "").toLowerCase();
        
        int left = 0;
        int right = str.length() - 1;

        while (left <= right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false; // If characters don't match, it's not a palindrome
            }
            left++;
            right--;
        }

        return true; // If the loop completes, it's a palindrome
    }
}
```
## 6. Create a program to calculate the area of a circle.

```java
import java.util.Scanner;

public class CircleAreaCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the radius of the circle: ");
        double radius = scanner.nextDouble();
        
        // Calculate the area of the circle
        double area = calculateCircleArea(radius);
        
        System.out.println("The area of the circle with a radius of " + radius + " is: " + area);
    }
    
    public static double calculateCircleArea(double radius) {
        // Calculate the area using the formula A = π * r^2
        double area = Math.PI * Math.pow(radius, 2);
        return area;
    }
}
```
## 7. Write a Java program to print the Fibonacci series.
```java
public class FibonacciSeries {
    public static void main(String[] args) {
        int n = 10; // Change this value to determine how many Fibonacci numbers you want to print

        int first = 0, second = 1;

        System.out.println("Fibonacci Series (first " + n + " numbers):");

        for (int i = 0; i < n; i++) {
            System.out.print(first + " ");
            int next = first + second;
            first = second;
            second = next;
        }
    }
}
```

## 8. Implement a program to check if a number is even or odd.
```java
import java.util.Scanner;

public class EvenOddChecker {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int number = scanner.nextInt();
        
        if (isEven(number)) {
            System.out.println(number + " is even.");
        } else {
            System.out.println(number + " is odd.");
        }
        
        scanner.close();
    }

    public static boolean isEven(int number) {
        return (number % 2) == 0;
    }
}
```
## 9.  Create a program to find the largest element in an array.
```java
public class FindLargestElement {

    public static void main(String[] args) {
        int[] array = {12, 34, 45, 9, 67, 99, 56, 83};
        
        int largest = findLargestElement(array);
        
        System.out.println("The largest element in the array is: " + largest);
    }

    public static int findLargestElement(int[] arr) {
        if (arr.length == 0) {
            throw new IllegalArgumentException("Array is empty");
        }
        
        int largest = arr[0]; // Initialize with the first element

        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > largest) {
                largest = arr[i];
            }
        }

        return largest;
    }
}
```

## 10. Write a program to find the second largest element in an array.

```java
public class FindSecondLargestElement {

    public static void main(String[] args) {
        int[] array = {12, 34, 45, 9, 67, 99, 56, 83};
        
        int secondLargest = findSecondLargestElement(array);
        
        System.out.println("The second largest element in the array is: " + secondLargest);
    }

    public static int findSecondLargestElement(int[] arr) {
        if (arr.length < 2) {
            throw new IllegalArgumentException("Array should contain at least two elements");
        }
        
        int largest = arr[0];
        int secondLargest = Integer.MIN_VALUE; // Initialize with the smallest possible value

        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > largest) {
                secondLargest = largest;
                largest = arr[i];
            } else if (arr[i] > secondLargest && arr[i] != largest) {
                secondLargest = arr[i];
            }
        }

        if (secondLargest == Integer.MIN_VALUE) {
            throw new IllegalArgumentException("There is no second largest element.");
        }

        return secondLargest;
    }
}
```
## 11. Implement a program to calculate the sum of digits in a number.
```java
import java.util.Scanner;

public class SumOfDigits {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a number: ");
        long number = scanner.nextLong();
        scanner.close();

        int sum = calculateSumOfDigits(number);
        System.out.println("Sum of digits: " + sum);
    }

    public static int calculateSumOfDigits(long number) {
        int sum = 0;

        while (number != 0) {
            // Get the last digit of the number by taking the remainder when divided by 10
            int digit = (int) (number % 10);
            
            // Add the digit to the sum
            sum += digit;
            
            // Remove the last digit from the number
            number /= 10;
        }

        return sum;
    }
}
```

## 12. Write a Java program to find the square root of a number.
```java
import java.util.Scanner;

public class SquareRootCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a number: ");
        double number = scanner.nextDouble();
        scanner.close();

        if (number < 0) {
            System.out.println("Square root is not defined for negative numbers.");
        } else {
            double squareRoot = Math.sqrt(number);
            System.out.println("Square root of " + number + " is: " + squareRoot);
        }
    }
}
```

## 13. Create a program to calculate the power of a number.
```java
import java.util.Scanner;

public class PowerCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the base number: ");
        double base = scanner.nextDouble();
        System.out.print("Enter the exponent: ");
        int exponent = scanner.nextInt();
        scanner.close();

        double result = calculatePower(base, exponent);
        System.out.println(base + " raised to the power of " + exponent + " is: " + result);
    }

    public static double calculatePower(double  base, int exponent) {
        double result = 1;

        for (int i = 0; i < Math.abs(exponent); i++) {
            result *= base;
        }

        if (exponent < 0) {
            // If the exponent is negative, calculate the reciprocal
            result = 1.0 / result;
        }

        return result;
    }
}
```

## 14. Implement a program to reverse an array.
```java
import java.util.Arrays;

public class ArrayReversal {
    public static void main(String[] args) {
        int[] originalArray = {1, 2, 3, 4, 5};

        System.out.println("Original Array: " + Arrays.toString(originalArray));

        int[] reversedArray = reverseArray(originalArray);

        System.out.println("Reversed Array: " + Arrays.toString(reversedArray));
    }

    public static int[] reverseArray(int[] arr) {
        int start = 0;
        int end = arr.length - 1;

        while (start < end) {
            // Swap the elements at the start and end indices
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;

            // Move towards the center of the array
            start++;
            end--;
        }
 
        return arr;
    }
}
```

## 15. Write a program to check if two strings are anagrams.
```java
import java.util.Arrays;

public class AnagramChecker {
    public static void main(String[] args) {
        String str1 = "listen";
        String str2 = "silent";

        if (areAnagrams(str1, str2)) {
            System.out.println(str1 + " and " + str2 + " are anagrams.");
        } else {
            System.out.println(str1 + " and " + str2 + " are not anagrams.");
        }
    }

    public static boolean areAnagrams(String str1, String str2) {
        // Remove spaces and convert strings to lowercase for case-insensitive comparison
        str1 = str1.replaceAll("\\s", "").toLowerCase();
        str2 = str2.replaceAll("\\s", "").toLowerCase();

        // Check if the lengths of the two strings are different
        if (str1.length() != str2.length()) {
            return false;
        }

        // Convert the strings to character arrays and sort them
        char[] charArray1 = str1.toCharArray();
        char[] charArray2 = str2.toCharArray();
        Arrays.sort(charArray1);
        Arrays.sort(charArray2);

        // Compare the sorted character arrays
        return Arrays.equals(charArray1, charArray2);
    }
}
```

## 16. Create a program to generate random numbers within a range.
```java
import java.util.Random;
import java.util.Scanner;

public class RandomNumberGenerator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the lower bound of the range: ");
        int lowerBound = scanner.nextInt();

        System.out.print("Enter the upper bound of the range: ");
        int upperBound = scanner.nextInt();

        if (lowerBound >= upperBound) {
            System.out.println("Invalid range. The lower bound must be less than the upper bound.");
            return;
        }

        System.out.print("Enter the number of random numbers to generate: ");
        int numRandomNumbers = scanner.nextInt();

        scanner.close();

        Random random = new Random();

        System.out.println("Random numbers within the specified range:");

        for (int i = 0; i < numRandomNumbers; i++) {
            int randomNumber = random.nextInt(upperBound - lowerBound + 1) + lowerBound;
            System.out.println(randomNumber);
        }
    }
}
```

## 17. Write a Java program to compute the greatest common divisor (GCD) of two numbers.
```java
import java.util.Scanner;

public class GCDCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the first number: ");
        int num1 = scanner.nextInt();
        System.out.print("Enter the second number: ");
        int num2 = scanner.nextInt();

        int gcd = calculateGCD(num1, num2);

        System.out.println("The GCD of " + num1 + " and " + num2 + " is: " + gcd);
    }

    // Function to calculate the GCD using the Euclidean algorithm
    public static int calculateGCD(int a, int b) {
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }
}
```

## 18. Implement a program to count the number of vowels and consonants in a string.
```java
import java.util.Scanner;

public class VowelConsonantCounter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String inputString = scanner.nextLine();

        int vowelCount = 0;
        int consonantCount = 0;

        // Convert the input string to lowercase for case-insensitive counting
        inputString = inputString.toLowerCase();

        for (int i = 0; i < inputString.length(); i++) {
            char ch = inputString.charAt(i);

            if (ch >= 'a' && ch <= 'z') {
                if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
                    vowelCount++;
                } else {
                    consonantCount++;
                }
            }
        }

        System.out.println("Number of vowels: " + vowelCount);
        System.out.println("Number of consonants: " + consonantCount);
    }
}
```

## 19. Create a program to remove duplicate elements from an array.
```java
import java.util.Arrays;

public class RemoveDuplicatesFromArray {
    public static void main(String[] args) {
        int[] originalArray = {1, 2, 2, 3, 4, 4, 5, 6, 6, 7};

        // Sort the original array to group duplicate elements together
        Arrays.sort(originalArray);

        int length = originalArray.length;
        int[] uniqueArray = new int[length];
        int uniqueCount = 0;

        for (int i = 0; i < length - 1; i++) {
            if (originalArray[i] != originalArray[i + 1]) {
                uniqueArray[uniqueCount] = originalArray[i];
                uniqueCount++;
            }
        }

        // Add the last element of the sorted array
        uniqueArray[uniqueCount] = originalArray[length - 1];
        uniqueCount++;

        // Create a new array with the unique elements
        int[] resultArray = Arrays.copyOf(uniqueArray, uniqueCount);

        System.out.println("Original Array: " + Arrays.toString(originalArray));
        System.out.println("Array with Duplicates Removed: " + Arrays.toString(resultArray));
    }
}
```

## 20. Write a program to count the occurrences of a character in a string.
```java
import java.util.Scanner;

public class CharacterOccurrenceCounter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String inputString = scanner.nextLine();

        System.out.print("Enter the character to count: ");
        char targetCharacter = scanner.next().charAt(0);

        int count = countOccurrences(inputString, targetCharacter);

        System.out.println("The character '" + targetCharacter + "' appears " + count + " times in the string.");
    }

    public static int countOccurrences(String inputString, char targetCharacter) {
        int count = 0;

        for (int i = 0; i < inputString.length(); i++) {
            if (inputString.charAt(i) == targetCharacter) {
                count++;
            }
        }

        return count;
    }
}
```

## 21. Implement a program to convert a decimal number to binary.
```java
import java.util.Scanner;

public class DecimalToBinary {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input decimal number
        System.out.print("Enter a decimal number: ");
        int decimalNumber = scanner.nextInt();

        // Convert to binary
        String binaryString = convertToBinary(decimalNumber);

        // Display the result
        System.out.println("Binary representation: " + binaryString);

        scanner.close();
    }

    // Function to convert decimal to binary
    private static String convertToBinary(int decimalNumber) {
        StringBuilder binary = new StringBuilder();

        while (decimalNumber > 0) {
            // Append the remainder to the binary string
            binary.insert(0, decimalNumber % 2);

            // Divide the decimal number by 2
            decimalNumber /= 2;
        }

        // If the input decimal number was 0
        if (binary.length() == 0) {
            binary.append(0);
        }

        return binary.toString();
    }
}
```

## 22. Create a program to find the intersection of two arrays.
```java
import java.util.Arrays;
import java.util.HashSet;

public class ArrayIntersection {
    public static void main(String[] args) {
        int[] array1 = {1, 2, 4, 5, 6};
        int[] array2 = {2, 3, 5, 7};

        int[] intersection = findIntersection(array1, array2);

        System.out.println("Array 1: " + Arrays.toString(array1));
        System.out.println("Array 2: " + Arrays.toString(array2));
        System.out.println("Intersection: " + Arrays.toString(intersection));
    }

    // Function to find the intersection of two arrays
    private static int[] findIntersection(int[] array1, int[] array2) {
        HashSet<Integer> set1 = new HashSet<>();
        HashSet<Integer> resultSet = new HashSet<>();

        // Add elements of array1 to set1
        for (int num : array1) {
            set1.add(num);
        }

        // Check for common elements in array2 and add to resultSet
        for (int num : array2) {
            if (set1.contains(num)) {
                resultSet.add(num);
            }
        }

        // Convert the resultSet to an array
        int[] intersection = new int[resultSet.size()];
        int index = 0;
        for (int num : resultSet) {
            intersection[index++] = num;
        }

        return intersection;
    }
}
```
## 23. Write a Java program to check if a number is a perfect number.
```java
import java.util.Scanner;

public class PerfectNumber {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input number
        System.out.print("Enter a number: ");
        int number = scanner.nextInt();

        // Check if the number is perfect
        boolean isPerfect = checkPerfectNumber(number);

        // Display the result
        if (isPerfect) {
            System.out.println(number + " is a perfect number.");
        } else {
            System.out.println(number + " is not a perfect number.");
        }

        scanner.close();
    }

    // Function to check if a number is a perfect number
    private static boolean checkPerfectNumber(int number) {
        if (number <= 1) {
            return false;
        }

        int sum = 1; // Start with 1 as every number is divisible by 1

        // Find the proper divisors and add them to the sum
        for (int i = 2; i <= Math.sqrt(number); i++) {
            if (number % i == 0) {
                sum += i;
                if (i != number / i) {
                    sum += number / i;
                }
            }
        }

        // Check if the sum of proper divisors equals the original number
        return sum == number;
    }
}
```
## 24. Implement a program to find the LCM (Least Common Multiple) of two numbers.
```java
import java.util.Scanner;

public class LCMCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input two numbers
        System.out.print("Enter the first number: ");
        int number1 = scanner.nextInt();

        System.out.print("Enter the second number: ");
        int number2 = scanner.nextInt();

        // Calculate and display the LCM
        int lcm = calculateLCM(number1, number2);
        System.out.println("LCM of " + number1 + " and " + number2 + " is: " + lcm);

        scanner.close();
    }

    // Function to calculate the LCM of two numbers
    private static int calculateLCM(int num1, int num2) {
        return (num1 * num2) / calculateGCD(num1, num2);
    }

    // Function to calculate the Greatest Common Divisor (GCD) using Euclidean algorithm
    private static int calculateGCD(int a, int b) {
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }
}
// Enter the first number: 12
// Enter the second number: 18
// LCM of 12 and 18 is: 36

```
## 25. Create a program to calculate the area of a triangle.
```java
import java.util.Scanner;

public class TriangleAreaCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input base and height
        System.out.print("Enter the base of the triangle: ");
        double base = scanner.nextDouble();

        System.out.print("Enter the height of the triangle: ");
        double height = scanner.nextDouble();

        // Calculate and display the area
        double area = calculateTriangleArea(base, height);
        System.out.println("The area of the triangle is: " + area);

        scanner.close();
    }

    // Function to calculate the area of a triangle
    private static double calculateTriangleArea(double base, double height) {
        return 0.5 * base * height;
    }
}
```
## 26. Write a program to print a pattern of numbers or asterisks (e.g., a pyramid).
```java
import java.util.Scanner;

public class NumberPyramid {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input the number of rows for the pyramid
        System.out.print("Enter the number of rows for the pyramid: ");
        int numRows = scanner.nextInt();

        // Print the number pyramid
        printNumberPyramid(numRows);

        scanner.close();
    }

    // Function to print a number pyramid
    private static void printNumberPyramid(int numRows) {
        for (int i = 1; i <= numRows; i++) {
            // Print spaces before the numbers
            for (int j = 1; j <= numRows - i; j++) {
                System.out.print("  ");
            }

            // Print ascending numbers
            for (int j = 1; j <= i; j++) {
                System.out.print(j + " ");
            }

            // Print descending numbers
            for (int j = i - 1; j >= 1; j--) {
                System.out.print(j + " ");
            }

            // Move to the next line after completing each row
            System.out.println();
        }
    }
}
```
## 27. Implement a program to find the factors of a number.
```java
import java.util.Scanner;

public class FactorsFinder {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input the number
        System.out.print("Enter a number: ");
        int number = scanner.nextInt();

        // Find and display the factors
        System.out.println("Factors of " + number + " are: ");
        findFactors(number);

        scanner.close();
    }

    // Function to find and print factors of a number
    private static void findFactors(int number) {
        for (int i = 1; i <= number; i++) {
            // Check if i is a factor of the given number
            if (number % i == 0) {
                System.out.print(i + " ");
            }
        }
    }
}
// Enter a number: 12
// Factors of 12 are: 
// 1 2 3 4 6 12
```
## 28. Create a program to check if a year is a leap year.
```java
import java.util.Scanner;

public class LeapYearChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input the year
        System.out.print("Enter a year: ");
        int year = scanner.nextInt();

        // Check and display if the year is a leap year
        if (isLeapYear(year)) {
            System.out.println(year + " is a leap year.");
        } else {
            System.out.println(year + " is not a leap year.");
        }

        scanner.close();
    }

    // Function to check if a year is a leap year
    private static boolean isLeapYear(int year) {
        if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
            return true;
        } else {
            return false;
        }
    }
}
```
## 29. Write a Java program to calculate the average of an array.
```java
import java.util.Scanner;

public class ArrayAverageCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input the size of the array
        System.out.print("Enter the size of the array: ");
        int size = scanner.nextInt();

        // Input array elements
        int[] array = new int[size];
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < size; i++) {
            System.out.print("Element " + (i + 1) + ": ");
            array[i] = scanner.nextInt();
        }

        // Calculate and display the average
        double average = calculateArrayAverage(array);
        System.out.println("The average of the array is: " + average);

        scanner.close();
    }

    // Function to calculate the average of an array
    private static double calculateArrayAverage(int[] array) {
        int sum = 0;

        // Calculate the sum of array elements
        for (int num : array) {
            sum += num;
        }

        // Calculate the average
        return (double) sum / array.length;
    }
}
```

## 30. Implement a program to reverse words in a sentence.
```java
import java.util.Scanner;

public class ReverseWordsInSentence {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input the sentence
        System.out.print("Enter a sentence: ");
        String sentence = scanner.nextLine();

        // Reverse and display the words in the sentence
        String reversedSentence = reverseWords(sentence);
        System.out.println("Reversed sentence: " + reversedSentence);

        scanner.close();
    }

    // Function to reverse the order of words in a sentence
    private static String reverseWords(String sentence) {
        String[] words = sentence.split("\\s+"); // Split the sentence into words
        StringBuilder reversedSentence = new StringBuilder();

        // Append words in reverse order to the StringBuilder
        for (int i = words.length - 1; i >= 0; i--) {
            reversedSentence.append(words[i]).append(" ");
        }

        return reversedSentence.toString().trim(); // Remove trailing space and return the result
    }
}
// Enter a sentence: Hello World, how are you today?
// Reversed sentence: today? you are how World, Hello
```
## 31. Create a program to find the missing number in an array of consecutive integers.
```java
public class FindMissingNumber {
    public static void main(String[] args) {
        int[] array = {1, 2, 3, 5, 6, 7, 8}; // Example array with a missing number

        int missingNumber = findMissingNumber(array);
        
        System.out.println("The missing number is: " + missingNumber);
    }

    static int findMissingNumber(int[] arr) {
        int n = arr.length + 1; // One number is missing
        int totalSum = n * (n + 1) / 2; // Sum of n natural numbers

        int actualSum = 0;
        for (int num : arr) {
            actualSum += num;
        }

        return totalSum - actualSum;
    }
}
```
## 32. Write a program to calculate the sum of natural numbers.
```java
import java.util.Scanner;

public class SumOfNaturalNumbers {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a positive integer: ");
        int n = scanner.nextInt();

        if (n <= 0) {
            System.out.println("Please enter a positive integer.");
        } else {
            int sum = calculateSum(n);
            System.out.println("The sum of natural numbers up to " + n + " is: " + sum);
        }

        scanner.close();
    }

    static int calculateSum(int num) {
        // Formula for sum of n natural numbers: sum = n * (n + 1) / 2
        return num * (num + 1) / 2;
    }
}
```
## 33. Implement a program to perform basic calculator operations (addition, subtraction, multiplication, division).
```java
import java.util.Scanner;

public class BasicCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the first number: ");
        double num1 = scanner.nextDouble();

        System.out.print("Enter the second number: ");
        double num2 = scanner.nextDouble();

        System.out.println("Select operation: ");
        System.out.println("1. Addition");
        System.out.println("2. Subtraction");
        System.out.println("3. Multiplication");
        System.out.println("4. Division");

        System.out.print("Enter choice (1-4): ");
        int choice = scanner.nextInt();

        double result = 0;

        switch (choice) {
            case 1:
                result = num1 + num2;
                break;
            case 2:
                result = num1 - num2;
                break;
            case 3:
                result = num1 * num2;
                break;
            case 4:
                if (num2 != 0) {
                    result = num1 / num2;
                } else {
                    System.out.println("Error: Cannot divide by zero.");
                    return;
                }
                break;
            default:
                System.out.println("Invalid choice. Please enter a number between 1 and 4.");
                return;
        }

        System.out.println("Result: " + result);

        scanner.close();
    }
}
```
## 34. Create a program to convert a temperature from Fahrenheit to Celsius and vice versa.
```java
import java.util.Scanner;

public class TemperatureConverter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Temperature Converter");
        System.out.println("1. Fahrenheit to Celsius");
        System.out.println("2. Celsius to Fahrenheit");
        System.out.print("Enter your choice (1 or 2): ");

        int choice = scanner.nextInt();

        if (choice == 1) {
            System.out.print("Enter temperature in Fahrenheit: ");
            double fahrenheit = scanner.nextDouble();
            double celsius = fahrenheitToCelsius(fahrenheit);
            System.out.println("Temperature in Celsius: " + celsius);
        } else if (choice == 2) {
            System.out.print("Enter temperature in Celsius: ");
            double celsius = scanner.nextDouble();
            double fahrenheit = celsiusToFahrenheit(celsius);
            System.out.println("Temperature in Fahrenheit: " + fahrenheit);
        } else {
            System.out.println("Invalid choice. Please enter 1 or 2.");
        }

        scanner.close();
    }

    // Convert Fahrenheit to Celsius
    private static double fahrenheitToCelsius(double fahrenheit) {
        return (fahrenheit - 32) * 5 / 9;
    }

    // Convert Celsius to Fahrenheit
    private static double celsiusToFahrenheit(double celsius) {
        return (celsius * 9 / 5) + 32;
    }
}
```
## 35. Write a Java program to find the smallest of three numbers.
```java
import java.util.Scanner;

public class SmallestNumberFinder {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter three numbers:");
        System.out.print("Enter the first number: ");
        double num1 = scanner.nextDouble();

        System.out.print("Enter the second number: ");
        double num2 = scanner.nextDouble();

        System.out.print("Enter the third number: ");
        double num3 = scanner.nextDouble();

        double smallest = findSmallest(num1, num2, num3);

        System.out.println("The smallest number is: " + smallest);

        scanner.close();
    }

    // Method to find the smallest of three numbers
    private static double findSmallest(double num1, double num2, double num3) {
        double smallest = num1;

        if (num2 < smallest) {
            smallest = num2;
        }

        if (num3 < smallest) {
            smallest = num3;
        }

        return smallest;
    }
}
```
## 36. Implement a program to find the area of a rectangle.
```java
import java.util.Scanner;

public class RectangleAreaCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Rectangle Area Calculator");
        System.out.print("Enter the length of the rectangle: ");
        double length = scanner.nextDouble();

        System.out.print("Enter the width of the rectangle: ");
        double width = scanner.nextDouble();

        double area = calculateRectangleArea(length, width);

        System.out.println("The area of the rectangle is: " + area);

        scanner.close();
    }

    // Method to calculate the area of a rectangle
    private static double calculateRectangleArea(double length, double width) {
        return length * width;
    } 
}
```
## 37. Create a program to find the ASCII value of a character.
```java
import java.util.Scanner;

public class ASCIIValueFinder {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a character: ");
        char inputChar = scanner.next().charAt(0);

        int asciiValue = findASCIIValue(inputChar);

        System.out.println("The ASCII value of '" + inputChar + "' is: " + asciiValue);

        scanner.close();
    }

    // Method to find the ASCII value of a character
    private static int findASCIIValue(char character) {
        return (int) character;
    }
}
```
## 38. Write a program to find the HCF (Highest Common Factor) of two numbers.
```java
import java.util.Scanner;

public class HCFCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the first number: ");
        int num1 = scanner.nextInt();

        System.out.print("Enter the second number: ");
        int num2 = scanner.nextInt();

        int hcf = findHCF(num1, num2);

        System.out.println("The HCF of " + num1 + " and " + num2 + " is: " + hcf);

        scanner.close();
    }

    // Method to find the HCF of two numbers
    private static int findHCF(int num1, int num2) {
        while (num2 != 0) {
            int temp = num2;
            num2 = num1 % num2;
            num1 = temp;
        }
        return num1;
    }
}
```
## 39. Implement a program to check if a given year is a century year.
```java
import java.util.Scanner;

public class CenturyYearChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a year: ");
        int year = scanner.nextInt();

        if (isCenturyYear(year)) {
            System.out.println(year + " is a century year.");
        } else {
            System.out.println(year + " is not a century year.");
        }

        scanner.close();
    }

    // Method to check if a year is a century year
    private static boolean isCenturyYear(int year) {
        // Check if the year is divisible by 100
        if (year % 100 == 0) {
            // If divisible by 100, check if it is also divisible by 400 to be a leap year
            return year % 400 == 0;
        }
        return false;
    }
}
```
## 40. Create a program to generate the first 'n' prime numbers.
```java
import java.util.Scanner;

public class PrimeNumberGenerator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the value of 'n': ");
        int n = scanner.nextInt();

        if (n > 0) {
            System.out.println("The first " + n + " prime numbers are:");
            printFirstNPrimes(n);
        } else {
            System.out.println("Please enter a positive integer for 'n'.");
        }

        scanner.close();
    }

    // Method to check if a number is prime
    private static boolean isPrime(int num) {
        if (num <= 1) {
            return false;
        }
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }

    // Method to print the first 'n' prime numbers
    private static void printFirstNPrimes(int n) {
        int count = 0;
        int num = 2; // Starting from the first prime number

        while (count < n) {
            if (isPrime(num)) {
                System.out.print(num + " ");
                count++;
            }
            num++;
        }
    }
}
```
## 41. Write a Java program to find the sum of all even numbers in a given range.
```java
import java.util.Scanner;

public class SumOfEvenNumbers {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the starting number of the range: ");
        int start = scanner.nextInt();

        System.out.print("Enter the ending number of the range: ");
        int end = scanner.nextInt();

        int sum = findSumOfEvenNumbers(start, end);

        System.out.println("The sum of even numbers in the range [" + start + ", " + end + "] is: " + sum);

        scanner.close();
    }

    // Method to find the sum of even numbers in a given range
    private static int findSumOfEvenNumbers(int start, int end) {
        int sum = 0;

        // Ensure the start number is even
        if (start % 2 != 0) {
            start++;
        }

        for (int i = start; i <= end; i += 2) {
            sum += i;
        }

        return sum;
    }   
}
```
## 42. Implement a program to print the multiplication table for a given number.
```java
import java.util.Scanner;

public class MultiplicationTable {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number to print its multiplication table: ");
        int number = scanner.nextInt();

        printMultiplicationTable(number);

        scanner.close();
    }

    // Method to print the multiplication table for a given number
    private static void printMultiplicationTable(int number) {
        System.out.println("Multiplication Table for " + number + ":");
        for (int i = 1; i <= 10; i++) {
            System.out.println(number + " x " + i + " = " + (number * i));
        }
    }
}
```
## 43. Create a program to generate a random password with a specified length.
```java
import java.security.SecureRandom;

public class RandomPasswordGenerator {
    public static void main(String[] args) {
        int passwordLength = 12; // Specify the desired password length
        String randomPassword = generateRandomPassword(passwordLength);

        System.out.println("Generated Random Password: " + randomPassword);
    }

    // Method to generate a random password
    private static String generateRandomPassword(int length) {
        String uppercaseLetters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        String lowercaseLetters = "abcdefghijklmnopqrstuvwxyz";
        String numbers = "0123456789";
        String specialCharacters = "!@#$%^&*()-_+=<>?";

        String allCharacters = uppercaseLetters + lowercaseLetters + numbers + specialCharacters;

        SecureRandom random = new SecureRandom();
        StringBuilder password = new StringBuilder();

        for (int i = 0; i < length; i++) {
            int randomIndex = random.nextInt(allCharacters.length());
            char randomChar = allCharacters.charAt(randomIndex);
            password.append(randomChar);
        }

        return password.toString();
    }
}
```
## 44. Write a program to reverse a sentence without reversing the words.
```java
import java.util.Scanner;

public class ReverseSentence {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a sentence: ");
        String inputSentence = scanner.nextLine();

        String reversedSentence = reverseSentenceWithoutWords(inputSentence);

        System.out.println("Reversed Sentence without Reversing Words: " + reversedSentence);

        scanner.close();
    }

    // Method to reverse a sentence without reversing the words
    private static String reverseSentenceWithoutWords(String sentence) {
        String[] words = sentence.split(" ");
        StringBuilder reversedSentence = new StringBuilder();

        for (int i = words.length - 1; i >= 0; i--) {
            reversedSentence.append(words[i]).append(" ");
        }

        return reversedSentence.toString().trim();
    }
}
```

## 45. Create a program to check if a string contains only digits.
```java
import java.util.Scanner;

public class CheckDigitsInString {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String inputString = scanner.nextLine();

        if (containsOnlyDigits(inputString)) {
            System.out.println("The string contains only digits.");
        } else {
            System.out.println("The string does not contain only digits.");
        }

        scanner.close();
    }

    // Method to check if a string contains only digits
    private static boolean containsOnlyDigits(String str) {
        // Using regular expression to check if the string contains only digits
        return str.matches("\\d+");
    }
}
```
## 46. Write a Java program to convert a binary number to a decimal number.
```java
import java.util.Scanner;

public class BinaryToDecimalConverter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a binary number: ");
        String binaryNumber = scanner.nextLine();

        int decimalNumber = convertBinaryToDecimal(binaryNumber);

        System.out.println("Decimal Equivalent: " + decimalNumber);

        scanner.close();
    }

    // Method to convert a binary number to a decimal number
    private static int convertBinaryToDecimal(String binary) {
        int decimalNumber = 0;
        int power = 0;

        for (int i = binary.length() - 1; i >= 0; i--) {
            char digit = binary.charAt(i);
            if (digit == '1') {
                decimalNumber += Math.pow(2, power);
            }
            power++;
        }

        return decimalNumber;
    }
}
```
## 47. Implement a program to print the Pascal's triangle.
```java
import java.util.Scanner;

public class PascalsTriangle {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of rows for Pascal's Triangle: ");
        int numRows = scanner.nextInt();

        printPascalsTriangle(numRows);

        scanner.close();
    }

    // Method to print Pascal's Triangle
    private static void printPascalsTriangle(int numRows) {
        for (int i = 0; i < numRows; i++) {
            int number = 1;
            for (int j = 0; j <= i; j++) {
                System.out.print(number + " ");
                number = number * (i - j) / (j + 1);
            }
            System.out.println();
        }
    }
}
```
## 48. Create a program to calculate the area and circumference of a circle using a class.
```java
import java.util.Scanner;

class Circle {
    double radius;

    // Constructor to initialize the radius
    public Circle(double radius) {
        this.radius = radius;
    }

    // Method to calculate the area of the circle
    double calculateArea() {
        return Math.PI * radius * radius;
    }

    // Method to calculate the circumference of the circle
    double calculateCircumference() {
        return 2 * Math.PI * radius;
    }
}

public class CircleCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the radius of the circle: ");
        double radius = scanner.nextDouble();

        // Create an instance of the Circle class
        Circle circle = new Circle(radius);

        // Calculate and display the area
        double area = circle.calculateArea();
        System.out.println("Area of the circle: " + area);

        // Calculate and display the circumference
        double circumference = circle.calculateCircumference();
        System.out.println("Circumference of the circle: " + circumference);

        scanner.close();
    }
}
```
## 49. Write a program to check if a string is a valid email address.
```java
import java.util.Scanner;

public class EmailValidator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter an email address: ");
        String emailAddress = scanner.nextLine();

        if (isValidEmail(emailAddress)) {
            System.out.println(emailAddress + " is a valid email address.");
        } else {
            System.out.println(emailAddress + " is not a valid email address.");
        }

        scanner.close();
    }

    // Method to check if a string is a valid email address
    private static boolean isValidEmail(String email) {
        // Regular expression for a simple email validation
        String emailRegex = "^[a-zA-Z0-9_+&*-]+(?:\\.[a-zA-Z0-9_+&*-]+)*@(?:[a-zA-Z0-9-]+\\.)+[a-zA-Z]{2,7}$";

        return email.matches(emailRegex);
    }
}
```