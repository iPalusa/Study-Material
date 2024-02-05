## Writing Challenges:

### 1. **Write a Java program to serialize and write a custom object to a binary file. Implement Serializable interface for the object.**
```java
import java.io.*;

// A simple custom object implementing the Serializable interface
class CustomObject implements Serializable {
    private static final long serialVersionUID = 1L; // Ensure version compatibility
    private String name;
    private int age;

    // Constructor
    public CustomObject(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter methods
    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}

public class ObjectSerializationExample {
    public static void main(String[] args) {
        // Create a custom object
        CustomObject objToSerialize = new CustomObject("John Doe", 25);

        // Define the file name
        String fileName = "serializedObject.bin";

        // Serialize and write the object to a binary file
        serializeObject(objToSerialize, fileName);

        System.out.println("Custom object serialized and written to " + fileName);
    }

    // Method to serialize and write the object to a binary file
    private static void serializeObject(CustomObject obj, String fileName) {
        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(fileName))) {
            // Write the object to the file
            oos.writeObject(obj);

        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
### 2. **Implement a binary file compression algorithm. Write compressed data to a binary file and later decompress it.**
`Method 1:`
```java
import java.io.*;
import java.util.zip.GZIPInputStream;
import java.util.zip.GZIPOutputStream;

public class Main {

    public static void main(String[] args) {
        String sourceFilePath = "D:\\Workspace\\Java\\Java Practise\\Sample Text Document.txt";
        String compressedFilePath = "D:\\Workspace\\Java\\Java Practise\\compressedBinaryFile.gz";
        String deCompressedFilePath = "D:\\Workspace\\Java\\Java Practise\\deCompressedBinaryFile.txt";

        compressFile(sourceFilePath, compressedFilePath);

        decompressFile(compressedFilePath, deCompressedFilePath);
    }

    public static void compressFile(String sourceFilePath, String compressedFilePath){
        try(FileInputStream fileInputStream = new FileInputStream(sourceFilePath);
        GZIPOutputStream gzipOutputStream = new GZIPOutputStream(new FileOutputStream(compressedFilePath))) {

            byte[] buffer = new byte[1024];
            int bytesRead;

            while((bytesRead = fileInputStream.read(buffer)) > 0){
                gzipOutputStream.write(buffer,0,bytesRead);
            }

            System.out.println("File compressed successfully");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    public static void decompressFile(String compressedFilePath, String decompressedFilePath){
        try(
            GZIPInputStream gzipInputStream = new GZIPInputStream(new FileInputStream(compressedFilePath));

            FileOutputStream fileOutputStream = new FileOutputStream(decompressedFilePath)
        ){
            byte[] buffer = new byte[1024];
            int bytesRead;

            while((bytesRead = gzipInputStream.read(buffer)) > 0){
                fileOutputStream.write(buffer,0,bytesRead);
            }

            System.out.println("File decompressed successfully");
        } catch (IOException e){
            e.printStackTrace();
        }
    }
}
/* 
    - gzipOutputStream.write(buffer, 0, bytesRead) writes the data from the buffer to a compressed output stream (GZIP).
    - 0 is the starting position in the buffer from where to start writing.
    - bytesRead is the number of bytes to write. It ensures that only the actual data read from the file is written, not any extra uninitialized bytes in the buffer.
 */
```
`Method 2: Run Length Encoding(RLE)`
```java
import java.io.*;

public class Main{
    public static int previousByte;
    public static void main(String[] args) {
        String sourceFilePath = "D:\\Workspace\\Java\\Java Practise\\Sample Text Document.txt";
        String compressedFilePath = "D:\\Workspace\\Java\\Java Practise\\CompressedBinary_RLE_.bin";
        String decompressedFilePath = "D:\\Workspace\\Java\\Java Practise\\DecompressedBinary_RLE_.txt";

        compressFile(sourceFilePath, compressedFilePath);
        DecompressFile(compressedFilePath, decompressedFilePath);
    }
// Compress Function
    public static void compressFile(String sourceFilePath, String compressedFilePath){
        try(
            FileInputStream fis = new FileInputStream(sourceFilePath);
            FileOutputStream fos = new FileOutputStream(compressedFilePath);
            ObjectOutputStream oos = new ObjectOutputStream(fos)
        ){
            int currentByte;
            int count = 1;
            boolean firstByte = true;

            while((currentByte = fis.read()) != -1){
                if(!firstByte){
                    if(currentByte == previousByte){
                        count++;
                    } else {
                        oos.writeInt(count);
                        oos.writeByte(previousByte);
                        count = 1;
                    }
                } else {
                    count = 1;
                    firstByte = false;
                }

                previousByte = currentByte;
            }

            oos.writeInt(count);
            oos.writeByte(previousByte);

            System.out.println("File Compressed Successfully");
        } catch (IOException e){
            e.printStackTrace();
        }
    }
    //Decompress Function
    public static void DecompressFile(String compressedFilePath, String decompressedFilePath){
        try(
            ObjectInputStream ois = new ObjectInputStream(new FileInputStream(compressedFilePath));
            FileOutputStream fos = new FileOutputStream(decompressedFilePath);
        ){
            while(true){
                try{
                    int count = ois.readInt();
                    byte value = ois.readByte();

                    for( int i=0;i< count;i++){
                        fos.write(value);
                    }
                } catch (IOException e){
                    break;
                }
            }
            System.out.println("File Decompressed Successfully");
        } catch (IOException e){
            e.printStackTrace();
        }
    }
}
```

### Reading Challenges:

6. **Read and parse a binary file containing 3D coordinates of points. Calculate the distance between each pair of points and write the results to a new binary file.**

7. **Write a program to read a binary file containing information about multiple books, including title, author, and publication date. Print the details of the books published in a specific year.**

8. **Implement a binary file parser for a custom file format. The file should contain a header, metadata, and data blocks. Extract and print information from each section.**

9. **Read a binary file that stores a large matrix of integers. Perform matrix operations (e.g., transpose, multiplication) and write the results to a new binary file.**

10. **Create a binary file containing audio samples. Read the file and perform operations like filtering or adding echo effects on the audio data. Write the modified data to a new binary file.**

### Combined Challenges:

11. **Implement a program that reads a binary file containing a serialized object, modifies the object, and writes it back to the file.**

12. **Write a binary file that represents a simple database. Each record in the file corresponds to a person with attributes like name, age, and address. Implement search and update functionalities.**

13. **Create a binary file containing multiple images. Implement a program that reads the file, performs image processing (e.g., resizing or filtering), and writes the modified images back to a new binary file.**

14. **Develop a binary file format for storing graph data (nodes and edges). Implement a program to read the file, perform graph algorithms, and write the results to a new binary file.**

15. **Implement a binary file merge program that reads two sorted binary files and merges them into a new sorted binary file.**