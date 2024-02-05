# Strings Methods

### String Creation:

1. **Creating a String:**
   ```javascript
   let str1 = "Hello, World!";
   let str2 = String(42);
   ```

### String Properties:

2. **Length:**
   ```javascript
   let length = str.length;
   ```

### Accessing Characters:

3. **charAt(index):**
   ```javascript
   let char = str.charAt(0);
   ```

4. **charCodeAt(index):**
   ```javascript
   let charCode = str.charCodeAt(0);
   ```

### Substrings:

5. **substring(startIndex, endIndex):**
   ```javascript
   let substring = str.substring(0, 5);
   ```

6. **slice(startIndex, endIndex):**
   ```javascript
   let sliced = str.slice(0, 5);
   ```

### Searching and Matching:

7. **indexOf(searchString, startIndex):**
   ```javascript
   let index = str.indexOf("lo");
   ```

8. **lastIndexOf(searchString, startIndex):**
   ```javascript
   let lastIndex = str.lastIndexOf("o");
   ```

9. **startsWith(searchString):**
   ```javascript
   let startsWithHello = str.startsWith("Hello");
   ```

10. **endsWith(searchString):**
    ```javascript
    let endsWithWorld = str.endsWith("World!");
    ```

11. **includes(searchString):**
    ```javascript
    let includesHello = str.includes("Hello");
    ```

### Case Transformation:

12. **toUpperCase():**
    ```javascript
    let upperCase = str.toUpperCase();
    ```

13. **toLowerCase():**
    ```javascript
    let lowerCase = str.toLowerCase();
    ```

### Trimming:

14. **trim():**
    ```javascript
    let trimmed = str.trim();
    ```

### Splitting and Joining:

15. **split(separator):**
    ```javascript
    let words = str.split(" ");
    ```

16. **join(separator):**
    ```javascript
    let joined = words.join("-");
    ```

### Replace:

17. **replace(oldValue, newValue):**
    ```javascript
    let replaced = str.replace("Hello", "Hi");
    ```

### Concatenation:

18. **concat(str2, str3, ...):**
    ```javascript
    let newString = str.concat(" ", "JavaScript");
    ```

### Template Literals:

19. **Template Literals:**
    ```javascript
    let name = "John";
    let greeting = `Hello, ${name}!`;
    ```


# Character Methods

1. **charAt(index):**
   - Returns the character at the specified index in a string.
   ```javascript
   const str = "Hello";
   const charAtIndex = str.charAt(1); // charAtIndex is "e"
   ```

2. **charCodeAt(index):**
   - Returns the Unicode value of the character at the specified index in a string.
   ```javascript
   const str = "Hello";
   const unicodeValue = str.charCodeAt(1); // unicodeValue is 101
   ```

3. **codePointAt(index):**
   - Returns the Unicode code point of the character at the specified index in a string.
   ```javascript
   const str = "🚀 Hello";
   const codePoint = str.codePointAt(0); // codePoint is 128640
   ```

4. **String.fromCodePoint(codePoint):**
   - Returns a string created from the specified Unicode code point.
   ```javascript
   const str = String.fromCodePoint(128640); // str is "🚀"
   ```

5. **concat(string2, string3, ...):**
   - Concatenates two or more strings.
   ```javascript
   const str1 = "Hello";
   const str2 = " World";
   const result = str1.concat(str2); // result is "Hello World"
   ```

6. **slice(startIndex, endIndex):**
   - Extracts a section of a string and returns a new string.
   ```javascript
   const str = "Hello World";
   const sliced = str.slice(0, 5); // sliced is "Hello"
   ```

7. **substring(startIndex, endIndex):**
   - Similar to slice, but doesn't accept negative indices.
   ```javascript
   const str = "Hello World";
   const subString = str.substring(0, 5); // subString is "Hello"
   ```

8. **substr(startIndex, length):**
   - Extracts a specified number of characters from a string, starting at a specified index.
   ```javascript
   const str = "Hello World";
   const subStr = str.substr(6, 5); // subStr is "World"
   ```

9. **toUpperCase():**
   - Converts all characters in a string to uppercase.
   ```javascript
   const str = "hello";
   const upperCaseStr = str.toUpperCase(); // upperCaseStr is "HELLO"
   ```

10. **toLowerCase():**
    - Converts all characters in a string to lowercase.
    ```javascript
    const str = "HELLO";
    const lowerCaseStr = str.toLowerCase(); // lowerCaseStr is "hello"
    ```

These are just a few of the many string methods available in JavaScript for working with characters and strings. Depending on your needs, you may find other methods like `trim()`, `charAt()`, and regular expressions useful as well.