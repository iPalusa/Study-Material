### 1. Implement a program that searches for a given substring in a text string and returns the index of the first occurrence.
```java
import java.util.Scanner;

public class Main{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter the String: ");
        String str = scanner.nextLine();

        System.out.println("Enter the substring to search for: ");
        String subString  = scanner.nextLine();
        
        int index = searchSubString(str,subString);

        if(index < -1){
            System.out.println("Substring not found in the text.");
        } else {
            System.out.println("Substring is found at index: "+ index);
        }
    }

    public static int searchSubString(String str, String subString){
        return str.indexOf(subString);
    }
}
```

### 2. **Substring Count:** Write a program to count the occurrences of a substring within a given text.
```java
public class Main{
    public static void main(String[] args) {
        String str = "This is a sample text. A sample text with a sample substring.";
        String subString = "sample";

        int count = countOccurences(str, subString);
        if(count < -1) {
            System.out.println("Substring is not found in text.");
        } else {
            System.out.println("Count Occurences of Substring '" +subString+ "' is: "+count);
        }
    }

    public static int countOccurences(String str, String subString){
        int count = 0;
        int index = str.indexOf(subString);

        while(index != -1){
            count++;
            index = str.indexOf(subString,index + 1);
        }
        return count;
    }
}
```

### 3. Implement a string search using regular expressions.
```java
import java.util.regex.Pattern;
import java.util.regex.Matcher;

/* 1. The regex approach provides more flexibility and power when searching for patterns beyond simple substrings.

2. The indexOf approach is simpler and more direct for basic substring searches, and it might be more suitable for certain scenarios.

3. Regular expressions are especially useful when you need to perform more complex string matching based on patterns or specific rules. */

public class Main{
    public static void main(String[] args) {
        String text = "This is a sample text. A sample text with a sample substring.";

        String subString = "sample";

        boolean found = searchString(text,subString);

        if(found){
            System.out.println("Substring is found.");
        } else{
            System.out.println("Substring is not found.");
        }

    }

    public static boolean searchString(String text, String subString){
        Pattern pattern = Pattern.compile(subString);
        Matcher matcher = pattern.matcher(text);

        return matcher.find();
    }
}
```
### 4. Create a program that searches for whole words in a text, not just substrings.
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class WholeWordSearch {

    public static void main(String[] args) {
        // Example text
        String text = "This is an example text with some words.";

        // Example word to search
        String word = "example";

        // Call the searchWholeWord method and display the result
        boolean found = searchWholeWord(text, word);

        if (found) {
            System.out.println("Word found in the text.");
        } else {
            System.out.println("Word not found in the text.");
        }
    }

    // Method to search for a whole word using regular expressions
    private static boolean searchWholeWord(String text, String word) {
        // Create a regular expression pattern with word boundaries
        Pattern pattern = Pattern.compile("\\b" + Pattern.quote(word) + "\\b");

        // Create a matcher for the text using the pattern
        Matcher matcher = pattern.matcher(text);

        // Use find() to search for the whole word
        return matcher.find();
    }
}
```
### 5. Develop a search algorithm that finds the last occurrence of a substring in a text.
```java
public class Main {
    public static void main(String[] args) {
        String text = "This is a sample text. A sample text with a sample substring.";

        // Example substring to search
        String substring = "sample";

        // Call the searchLastOccurrence method and display the result
        int lastIndex = searchLastOccurrence(text, substring);

        if (lastIndex != -1) {
            System.out.println("Last occurrence found at index: " + lastIndex);
        } else {
            System.out.println("Substring not found in the text.");
        }
    }
    public static int searchLastOccurrence(String text, String subString){
        int currentIndex = 0;
        int lastOccurenceIndex = -1;

        while((currentIndex = text.indexOf(subString, currentIndex)) != -1){
            lastOccurenceIndex = currentIndex;
            currentIndex += subString.length();
        }
        return lastOccurenceIndex;
    }
}
```
### 6. Identify and print all palindromic substrings in a given text.
```java

```
6. **Longest Common Substring:** Find the longest common substring between two input strings.

7. **Anagram Search:** Implement a program to search for anagrams of a given word in a text.

8.  **Wildcard Search:** Allow users to perform wildcard searches, where '*' can match any sequence of characters.

9.  **Levenshtein Distance:** Calculate and display the Levenshtein distance between two strings.

10. **Prefix Search:** Develop a program that searches for words starting with a given prefix.

11. **Suffix Search:** Create a program that finds words ending with a specified suffix.

12. **Edit Distance Search:** Implement a search algorithm based on the edit distance between two strings.

13. **Substring Replacement:** Write a program that replaces occurrences of a substring with another string in a given text.

14. **Consecutive Character Search:** Find the longest substring containing consecutive characters in alphabetical order.

15. **Vowel-Consonant Ratio:** Calculate and display the ratio of vowels to consonants in a given text.

16. **Word Frequency:** Count and display the frequency of each word in a given text.

17. **Unique Word Count:** Count the number of unique words in a text.

18. **CamelCase Search:** Identify and print words written in CamelCase in a given text.

19. **Numeric String Search:** Search for numeric strings in a given text.

20. **Morse Code Search:** Implement a program that searches for Morse code patterns in a given text.

21. **Unicode Character Search:** Write a program that searches for specific Unicode characters or character ranges in a text.

22. **Simultaneous Substring Search:** Allow users to input multiple substrings and find their occurrences in a text simultaneously.

23. **Rotational String Search:** Implement a search algorithm that detects rotated versions of a substring within a larger text.