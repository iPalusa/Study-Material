### 4. Rename a text file using the command line.
To rename a text file using the command line in Java, you can use the Files.move() method from the java.nio.file package.

### 7. List the contents of a directory using the command line.
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class ListDirectoryContents {

    public static void main(String[] args) {
        // Replace "path/to/your/directory" with the actual path of the directory you want to list
        String directoryPath = "path/to/your/directory";

        listDirectoryContents(directoryPath);
    }

    public static void listDirectoryContents(String directoryPath) {
        try {
            ProcessBuilder processBuilder;

            // Check if the system is Windows or Unix-like
            if (System.getProperty("os.name").startsWith("Windows")) {
                processBuilder = new ProcessBuilder("cmd", "/c", "dir", directoryPath);
            } else {
                processBuilder = new ProcessBuilder("ls", directoryPath);
            }

            Process process = processBuilder.start();

            // Read the output of the command
            BufferedReader reader = new BufferedReader(new InputStreamReader(process.getInputStream()));
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }

            // Wait for the command to complete
            int exitCode = process.waitFor();
            System.out.println("Command exited with code: " + exitCode);

        } catch (IOException | InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```
### 8. Navigate to a different directory using the command line.
### 9. Create a nested directory structure using the command line.
### 10. Move a file from one directory to another using the command line.
### 11. Copy all text files from one directory to another using the command line.
### 12. Display the size of a text file using the command line.
### 13. Display the size of a directory (including all its contents) using the command line.
### 14. Display the last modified timestamp of a text file using the command line.
### 15. Display the file permissions of a text file using the command line.
### 16. Create a backup of a text file using the command line.
### 17. Display the number of words in a text file using the command line.
### 18. Count the number of lines in a text file using the command line.
### 19. Search for a specific word in a text file using the command line.
### 20. Concatenate the content of two text files into a new file using the command line.
### 21. Sort the lines of a text file alphabetically using the command line.
### 22. Reverse the lines of a text file using the command line.
### 23. Display unique lines in a text file using the command line.
### 24. Replace a specific word with another word in a text file using the command line.
### 25. Extract lines containing a specific pattern from a text file using the command line.
### 26. Archive a directory using `tar` from the command line.
### 27. Compress a text file using `gzip` from the command line.
### 28. Decompress a compressed text file using `gzip` from the command line.
### 29. Create a ZIP archive of a directory using the command line.
### 30. Extract the contents of a ZIP archive using the command line.
### 31. Create a new text file with a specific encoding using the command line.
### 32. Convert the encoding of a text file using the `iconv` command from the command line.
### 33. Display the difference between two text files using the `diff` command from the command line.
### 34. Create a symbolic link to a text file using the command line.
### 35. Display information about a text file using the `stat` command from the command line.
### 36. Create a file with a specific timestamp using the `touch` command from the command line.
### 37. Create a text file with random content using the `dd` command from the command line.
### 38. Display the disk space usage of a directory using the `du` command from the command line.
### 39. Display the available disk space using the `df` command from the command line.
### 40. Archive and compress a directory using `tar` and `gzip` from the command line.
### 41. Create a new directory and its subdirectories using a single command from the command line.
### 42. Display the first 10 lines of a text file using the `head` command from the command line.
### 43. Display the last 10 lines of a text file using the `tail` command from the command line.
### 44. Count the occurrences of each word in a text file using the command line.
### 45. Extract specific columns from a CSV file using the `cut` command from the command line.
### 46. Replace tabs with spaces in a text file using the `expand` command from the command line.
### 47. Display the total number of files in a directory using the command line.
### 48. Display the total number of directories in a directory using the command line.
### 49. Display the total number of files and directories in a directory using the command line.
### 50. Find and display all empty files in a directory using the command line.
### 51. Find and display all hidden files in a directory using the command line.
### 52. Find and display all executable files in a directory using the command line.
### 53. Find and display all files modified within the last 7 days in a directory using the command line.
### 54. Find and display all files larger than 1 GB in a directory using the command line.
### 55. Find and display all files with a specific word in their name in a directory using the command line.
### 56. Find and display all files containing a specific word in their content in a directory using the command line.
### 57. Find and display all files with a specific pattern in their name using a regular expression from the command line.
### 58. Display the number of lines in the longest text file in a directory using the command line.
### 59. Rename all text files in a directory with a ".bak" extension to have a ".txt" extension using the command line.
### 60. Display
### 
###  the average size of a text file in a directory using the command line.
### 61. Display the names of all files in a directory sorted by size (ascending) using the command line.
### 62. Display the names of all directories in a directory sorted by the number of files they contain using the command line.
### 63. Find and display all files with the same content in a directory using the command line.
### 64. Display the percentage of files in a directory that are text files using the command line.
### 65. Display the names of all files in a directory with their extension converted to uppercase using the command line.
### 66. Create a new directory with the current timestamp as its name using the command line.
### 67. Copy the content of a directory to another directory, excluding all hidden files using the command line.
### 68. Display the names of all files in a directory that have not been modified in the last 30 days using the command line.
### 69. Remove all empty directories in a directory using the command line.
### 70. Display the names of all files in a directory that have more than 100 lines using the command line.
### 71. Display the names of all files in a directory that start with a vowel using the command line.
### 72. Archive all text files in a directory into separate ZIP files using the command line.
### 73. Create a text file with the names of all files in a directory using the command line.
### 74. Display the names of all files in a directory that are writable by the owner using the command line.
### 75. Display the names of all files in a directory that have read and write permissions for the owner using the command line.
### 76. Create a new directory with the names of all files in a directory, replacing spaces with underscores using the command line.
### 77. Create a text file with the names of all files in a directory and their respective sizes using the command line.
### 78. Display the names of all files in a directory that have been modified more than 5 times using the command line.
### 79. Display the names of all files in a directory that have been accessed within the last 14 days using the command line.
### 80. Display the names of all files in a directory that have been changed within the last 7 days using the command line.
### 81. Copy the content of a directory to another directory, preserving the directory structure using the command line.
### 82. Create a new directory with the names of all files in a directory, sorted alphabetically, using the command line.
### 83. Create a new directory with the names of all files in a directory, sorted by modification time, using the command line.
### 84. Display the names of all files in a directory that contain both uppercase and lowercase letters using the command line.
### 85. Display the names of all files in a directory that have a size between 1 KB and 1 MB using the command line.
### 86. Find and display all files in a directory that have names longer than 20 characters using the command line.
### 87. Display the names of all files in a directory that have names consisting only of digits using the command line.
### 88. Display the names of all files in a directory that have names consisting only of letters using the command line.
### 89. Display the names of all files in a directory that have names consisting only of alphanumeric characters using the command line.
### 90. Display the names of all files in a directory that have names consisting only of special characters using the command line.
### 91. Display the names of all files in a directory that have names containing spaces using the command line.
### 92. Create a new directory with the names of all files in a directory, removing any leading or trailing spaces in file names, using the command line.
### 93. Create a new directory with the names of all files in a directory, replacing spaces with underscores and converting all characters to lowercase using the command line.
### 94. Display the names of all files in a directory that have names starting with a digit using the command line.
### 95. Display the names of all files in a directory that have names starting with a letter using the command line.
### 96. Display the names of all files in a directory that have names starting with a vowel or a digit using the command line.
### 97. Create a new directory with the names of all files in a directory, excluding those with names starting with "temp_" using the command line.
### 98. Display the names of all files in a directory that have names containing at least three consecutive vowels using the command line.
### 99. Display the names of all files in a directory that have names containing a sequence of at least five consecutive digits using the command line.