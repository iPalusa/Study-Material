# Dequeues (Double-Ended Queues):

# I. Introduction to Dequeues
## A. Definition and Characteristics
A dequeue (pronounced "deck"), short for double-ended queue, is a versatile data structure that allows insertion and deletion of elements from both ends – the front and the rear. This makes it different from a standard queue, where elements are added at the rear and removed from the front. A dequeue combines the features of both stacks and queues, providing flexibility in managing elements.

### Characteristics of Dequeue:

1. **Double-Ended Nature:**
   - Dequeues support operations on both ends, allowing elements to be inserted or removed from both the front and the rear.

2. **Dynamic Size:**
   - Dequeues can dynamically grow or shrink based on the number of elements, making them suitable for various applications.

3. **Linear Structure:**
   - Elements in a dequeue are arranged in a linear or sequential order, just like in a queue or a stack.

4. **Versatility:**
   - Dequeues can function as both queues and stacks. Depending on the requirements, elements can be inserted or removed from either end, providing flexibility in how the data structure is used.

5. **Random Access:**
   - Some deque implementations may support random access to elements, allowing direct access to elements at specific positions.

6. **FIFO and LIFO:**
   - Dequeues can be used to follow both the First-In-First-Out (FIFO) principle (like a queue) and the Last-In-First-Out (LIFO) principle (like a stack), depending on the operations performed.

### Use Cases for Dequeues:

- **Palindromic Checking:**
  - Dequeues can be used to efficiently check whether a given string is a palindrome by comparing characters from both ends.

- **Sliding Window Problems:**
  - Dequeues are commonly used in algorithms that involve sliding windows, such as finding the maximum or minimum element in all subarrays of a given size.

- **Job Scheduling:**
  - Dequeues can be employed in scenarios where tasks need to be scheduled based on their priority, allowing efficient insertion and removal of tasks from both ends.
## B. Basic Operations
Basic operations on a dequeue (double-ended queue) involve inserting and removing elements from both the front and the rear. Dequeues support a variety of operations that make them versatile for different use cases. Here are the basic operations commonly associated with deques:

### 1. **Insertion at Front (`addFirst()` or `offerFirst()`):**
   - Adds an element to the front of the dequeue.
   - If the operation is successful, it returns true; otherwise, it throws an exception or returns false, depending on the implementation.

### 2. **Insertion at Rear (`addLast()` or `offerLast()`):**
   - Adds an element to the rear of the dequeue.
   - If the operation is successful, it returns true; otherwise, it throws an exception or returns false, depending on the implementation.

### 3. **Deletion from Front (`removeFirst()` or `pollFirst()`):**
   - Removes and returns the element from the front of the dequeue.
   - If the dequeue is empty, `removeFirst()` may throw an exception, while `pollFirst()` returns null.

### 4. **Deletion from Rear (`removeLast()` or `pollLast()`):**
   - Removes and returns the element from the rear of the dequeue.
   - If the dequeue is empty, `removeLast()` may throw an exception, while `pollLast()` returns null.

### 5. **Peek at Front (`getFirst()` or `peekFirst()`):**
   - Views the element at the front of the dequeue without removing it.
   - If the dequeue is empty, `getFirst()` may throw an exception, while `peekFirst()` returns null.

### 6. **Peek at Rear (`getLast()` or `peekLast()`):**
   - Views the element at the rear of the dequeue without removing it.
   - If the dequeue is empty, `getLast()` may throw an exception, while `peekLast()` returns null.

### 7. **Size (`size()`):**
   - Returns the number of elements in the dequeue.

### 8. **isEmpty (`isEmpty()`):**
   - Checks whether the dequeue is empty.
   - Returns true if the dequeue is empty; otherwise, returns false.

### Implementation Example in Java:

Here's a simple example using Java's `LinkedList` as a deque implementation:

```java
import java.util.LinkedList;
import java.util.Deque;

public class DequeExample {
    public static void main(String[] args) {
        Deque<Integer> deque = new LinkedList<>();

        // Inserting elements at both ends
        deque.addFirst(1);
        deque.addLast(2);
        deque.offerFirst(3);
        deque.offerLast(4);

        // Displaying the deque
        System.out.println("Deque: " + deque);

        // Removing elements from both ends
        int removedFromFront = deque.removeFirst();
        int removedFromRear = deque.removeLast();

        // Displaying the deque after removal
        System.out.println("Removed from Front: " + removedFromFront);
        System.out.println("Removed from Rear: " + removedFromRear);
        System.out.println("Deque after removal: " + deque);
    }
}
```

In this example:

- Elements are inserted at both ends using methods like `addFirst()`, `addLast()`, `offerFirst()`, and `offerLast()`.
- Elements are removed from both ends using methods like `removeFirst()` and `removeLast()`.
- The `size()` method is used to get the number of elements in the deque.
- The `isEmpty()` method checks whether the deque is empty.

# II. Types of Dequeues
## A. Input-Restricted Deque
An Input-Restricted Deque is a variation of a deque (double-ended queue) where certain restrictions are imposed on the allowable operations. In an input-restricted deque, elements can be added or removed only from one end, while the other end remains fixed or has limited access. This restriction adds specific characteristics to the deque, making it suitable for certain use cases.

### Characteristics of an Input-Restricted Deque:

1. **Limited Access:**
   - Only one end (either front or rear) allows insertions or removals, while the other end remains fixed or has limited access. This restriction simplifies the behavior of the deque.

2. **FIFO or LIFO Behavior:**
   - Depending on the specific restriction (front or rear), the deque may exhibit First-In-First-Out (FIFO) or Last-In-First-Out (LIFO) behavior.

3. **Useful in Specific Scenarios:**
   - Input-restricted deques are designed to address particular scenarios where the restricted access aligns with the requirements of the problem at hand.

4. **Simplification of Operations:**
   - The restriction simplifies the operations on the deque, making it easier to reason about and potentially improving the efficiency of certain algorithms.

### Example Implementation in Java:

Here's a simple example of an input-restricted deque in Java where elements can only be added or removed from the front:

```java
import java.util.LinkedList;
import java.util.Deque;

public class InputRestrictedDequeExample {
    public static void main(String[] args) {
        // Using LinkedList as the underlying structure
        LinkedList<Integer> inputRestrictedDeque = new LinkedList<>();

        // Adding elements to the front
        inputRestrictedDeque.addFirst(1);
        inputRestrictedDeque.addFirst(2);
        inputRestrictedDeque.addFirst(3);

        // Displaying the deque
        System.out.println("Input-Restricted Deque: " + inputRestrictedDeque);

        // Removing elements from the front
        int removedFromFront1 = inputRestrictedDeque.removeFirst();
        int removedFromFront2 = inputRestrictedDeque.removeFirst();

        // Displaying the deque after removals
        System.out.println("Removed from Front: " + removedFromFront1 + ", " + removedFromFront2);
        System.out.println("Input-Restricted Deque after removals: " + inputRestrictedDeque);
    }
}
```

In this example:

- Elements are added to the front of the deque using `addFirst()`.
- Elements are removed from the front using `removeFirst()`.
- The input-restricted deque exhibits FIFO behavior as elements are added and removed from the front.

## B. Output-Restricted Deque
An Output-Restricted Deque is a variation of a deque (double-ended queue) where certain restrictions are imposed on the allowable operations. In an output-restricted deque, elements can be added or removed only from one end, while the other end remains fixed or has limited access. This restriction adds specific characteristics to the deque, making it suitable for certain use cases.

### Characteristics of an Output-Restricted Deque:

1. **Limited Access:**
   - Only one end (either front or rear) allows insertions or removals, while the other end remains fixed or has limited access. This restriction simplifies the behavior of the deque.

2. **FIFO or LIFO Behavior:**
   - Depending on the specific restriction (front or rear), the deque may exhibit First-In-First-Out (FIFO) or Last-In-First-Out (LIFO) behavior.

3. **Useful in Specific Scenarios:**
   - Output-restricted deques are designed to address particular scenarios where the restricted access aligns with the requirements of the problem at hand.

4. **Simplification of Operations:**
   - The restriction simplifies the operations on the deque, making it easier to reason about and potentially improving the efficiency of certain algorithms.

### Example Implementation in Java:

Here's a simple example of an output-restricted deque in Java where elements can only be added or removed from the rear:

```java
import java.util.LinkedList;
import java.util.Deque;

public class OutputRestrictedDequeExample {
    public static void main(String[] args) {
        // Using LinkedList as the underlying structure
        LinkedList<Integer> outputRestrictedDeque = new LinkedList<>();

        // Adding elements to the rear
        outputRestrictedDeque.addLast(1);
        outputRestrictedDeque.addLast(2);
        outputRestrictedDeque.addLast(3);

        // Displaying the deque
        System.out.println("Output-Restricted Deque: " + outputRestrictedDeque);

        // Removing elements from the rear
        int removedFromRear1 = outputRestrictedDeque.removeLast();
        int removedFromRear2 = outputRestrictedDeque.removeLast();

        // Displaying the deque after removals
        System.out.println("Removed from Rear: " + removedFromRear1 + ", " + removedFromRear2);
        System.out.println("Output-Restricted Deque after removals: " + outputRestrictedDeque);
    }
}
```

In this example:

- Elements are added to the rear of the deque using `addLast()`.
- Elements are removed from the rear using `removeLast()`.
- The output-restricted deque exhibits LIFO behavior as elements are added and removed from the rear.

# III. Applications
## A. Palindrome Checking:

A palindrome is a sequence of characters that reads the same forward as backward. Deques are commonly used in palindrome checking algorithms. By using a deque, you can efficiently compare characters from both ends of a string, making it easy to determine whether the string is a palindrome.

Here's a simple Java example of palindrome checking using a deque:

```java
import java.util.ArrayDeque;
import java.util.Deque;

public class PalindromeChecker {
    public static boolean isPalindrome(String str) {
        // Creating a deque of characters
        Deque<Character> deque = new ArrayDeque<>();

        // Adding characters from the string to the deque
        for (char c : str.toCharArray()) {
            deque.add(c);
        }

        // Comparing characters from both ends of the deque
        while (deque.size() > 1) {
            if (!deque.removeFirst().equals(deque.removeLast())) {
                return false; // Not a palindrome
            }
        }

        return true; // Palindrome
    }

    public static void main(String[] args) {
        String palindromeStr = "radar";
        String nonPalindromeStr = "hello";

        System.out.println(palindromeStr + " is a palindrome: " + isPalindrome(palindromeStr));
        System.out.println(nonPalindromeStr + " is a palindrome: " + isPalindrome(nonPalindromeStr));
    }
}
```

In this example, the `isPalindrome` method uses a deque to compare characters from both ends of the string. The deque is initially populated with characters from the string, and then characters are removed from both ends until the deque is empty or only one character remains.

## B. Sliding Window Maximum:

Sliding window maximum problems involve finding the maximum value in a subarray of fixed size as it slides through an array. Deques can be used efficiently to solve sliding window maximum problems. The deque stores indices of elements in the current window in a way that ensures the maximum element is always at the front of the deque.

Here's a Java example illustrating sliding window maximum using a deque:

```java
import java.util.ArrayDeque;
import java.util.Deque;

public class SlidingWindowMaximum {
    public static int[] maxSlidingWindow(int[] nums, int k) {
        if (nums == null || nums.length == 0) {
            return new int[0];
        }

        int n = nums.length;
        int[] result = new int[n - k + 1];
        Deque<Integer> deque = new ArrayDeque<>();

        for (int i = 0; i < n; i++) {
            // Remove elements outside the current window
            while (!deque.isEmpty() && deque.peek() < i - k + 1) {
                deque.poll();
            }

            // Remove smaller elements in the current window
            while (!deque.isEmpty() && nums[deque.peekLast()] < nums[i]) {
                deque.pollLast();
            }

            deque.offer(i);

            // Add maximum element of the current window to the result array
            if (i >= k - 1) {
                result[i - k + 1] = nums[deque.peek()];
            }
        }

        return result;
    }

    public static void main(String[] args) {
        int[] nums = {1, 3, -1, -3, 5, 3, 6, 7};
        int k = 3;
        int[] result = maxSlidingWindow(nums, k);

        System.out.println("Sliding Window Maximum: " + Arrays.toString(result));
    }
}
```

In this example, the `maxSlidingWindow` method uses a deque to efficiently find the maximum element in each sliding window of size `k`. The deque stores indices, and its front always represents the maximum element in the current window.

## C. Undo Mechanism in Editors:

Deques are often used in implementing undo mechanisms in text editors. When a user performs an action (e.g., typing, deleting, formatting), the state of the document can be stored in a deque. If the user wants to undo an action, the most recent state can be retrieved from the deque and applied.

Here's a simplified illustration of an undo mechanism using a deque in Java:

```java
import java.util.ArrayDeque;
import java.util.Deque;

class Editor {
    private StringBuilder document;
    private Deque<StringBuilder> undoDeque;

    public Editor() {
        document = new StringBuilder();
        undoDeque = new ArrayDeque<>();
    }

    public void type(char c) {
        undoDeque.push(new StringBuilder(document));
        document.append(c);
    }

    public void delete() {
        if (document.length() > 0) {
            undoDeque.push(new StringBuilder(document));
            document.deleteCharAt(document.length() - 1);
        }
    }

    public void undo() {
        if (!undoDeque.isEmpty()) {
            document = undoDeque.pop();
        }
    }

    public String getDocument() {
        return document.toString();
    }
}

public class UndoMechanismExample {
    public static void main(String[] args) {
        Editor editor = new Editor();

        editor.type('H');
        editor.type('e');
        editor.type('l');
        editor.type('l');
        editor.type('o');

        System.out

.println("Document after typing: " + editor.getDocument());

        editor.delete();
        editor.delete();

        System.out.println("Document after deletion: " + editor.getDocument());

        editor.undo();

        System.out.println("Document after undo: " + editor.getDocument());
    }
}
```

In this example, the `Editor` class uses a deque (`undoDeque`) to store previous states of the document. The `type`, `delete`, and `undo` methods modify the document and update the deque accordingly. The undo mechanism allows reverting to the previous state of the document.