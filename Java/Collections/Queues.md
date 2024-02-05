
# I. Introduction to Queues
## A. Definition and Characteristics

### Queues:
A queue is a linear data structure that follows the First-In-First-Out (FIFO) principle, meaning that the first element added to the queue will be the first one to be removed. It represents a collection of elements with two main operations: enqueue (inserting an element at the rear) and dequeue (removing an element from the front).

#### Characteristics:
1. **FIFO Principle:**
   - The element that has been in the queue the longest is the first one to be removed.

2. **Enqueue Operation:**
   - Elements are added to the rear (end) of the queue.
  
3. **Dequeue Operation:**
   - Elements are removed from the front (beginning) of the queue.

4. **Linear Structure:**
   - Queues have a linear structure where elements are arranged in a specific order.

5. **Limited Access:**
   - Elements can only be added at the rear and removed from the front. No other access points are allowed.

6. **Basic Operations:**
   - Basic operations include enqueue, dequeue, peek (viewing the front element without removal), isEmpty, and size.

7. **Real-life Analogy:**
   - Similar to a real-life queue or line where people wait in order.

### Dequeues (Double-Ended Queues):
A dequeue (double-ended queue) is an extension of a queue that allows insertion and deletion at both ends. It combines the properties of stacks and queues, providing more flexibility in handling elements.

#### Characteristics:
1. **Front and Rear Insertion/Deletion:**
   - Elements can be inserted or deleted from both the front and the rear of the dequeue.

2. **Versatility:**
   - Dequeues can function as both queues and stacks, making them more versatile in certain scenarios.

3. **Linear Structure:**
   - Similar to queues, dequeues maintain a linear structure.

4. **Limited Access:**
   - Operations are primarily limited to front and rear access points.

5. **Basic Operations:**
   - Basic operations include insertFront, insertRear, deleteFront, deleteRear, peekFront, peekRear, isEmpty, and size.

6. **Comparison with Queues and Stacks:**
   - Dequeues combine features of both queues and stacks, allowing for more varied use cases.

7. **Applications:**
   - Dequeues are used in scenarios where elements need to be inserted or deleted from both ends, such as in sliding window problems or palindrome checking.
## B. Real-life examples

### Examples of Queues:

1. **Supermarket Checkout:**
   - Customers waiting in line to pay at the checkout form a queue. The first customer in line is served first.

2. **Print Queue:**
   - Print jobs sent to a printer are processed in the order they are received, creating a print queue.

3. **Call Centers:**
   - Incoming calls are typically placed in a queue, and customer service representatives attend to calls based on the order they were received.

4. **Ticket Counter:**
   - People waiting to purchase tickets for a movie, concert, or public transportation form a queue.

5. **Bakery or Cafe Queue:**
   - Customers waiting to place an order or receive their prepared items in a bakery or cafe create a queue.

6. **Task Processing:**
   - In multitasking operating systems, processes waiting to be executed are managed in a queue.

7. **Browsing History:**
   - Web browser tabs often operate on a queue system where the first tab opened is the first to be closed.

### Examples of Dequeues:

1. **Sliding Window in Data Streams:**
   - Deques are used to efficiently solve sliding window problems, where elements are added and removed from both ends.

2. **Undo Mechanism in Editors:**
   - A deque can be employed to implement an undo feature in text editors, allowing users to revert changes in the order they were made.

3. **Navigation System:**
   - Maps or navigation apps may use deques to manage the history of locations visited, allowing users to move backward and forward through their route.

4. **Palindrome Checking:**
   - A deque can be used to check whether a given sequence, such as a word, is a palindrome.

5. **Task Scheduling with Prioritization:**
   - In some task scheduling scenarios, deques are used to manage tasks with different priorities.

6. **Buffer Management in Operating Systems:**
   - Deques can be used in buffer management to efficiently manage data transfer between processes.

7. **Double-Ended Queues in Networking:**
   - Deques are employed in networking protocols where data needs to be inserted or removed from both ends efficiently.

## C. FIFO (First-In-First-Out) principle
The FIFO (First-In-First-Out) principle is a fundamental concept in computer science and queue data structures. It refers to the order in which elements are processed or served in a queue. In a system that follows the FIFO principle, the first element added to the queue is the first one to be removed.

Here are the key characteristics of the FIFO principle:

1. **Order of Processing:**
   - The order in which elements are enqueued (added) to the queue determines the order in which they are dequeued (removed).

2. **First-In-First-Out:**
   - The element that has been in the queue the longest is the first one to be processed or removed. It's analogous to waiting in line or standing in a queue in the physical world.

3. **Queue Operations:**
   - The FIFO principle is inherent in the basic operations of a queue. The enqueue operation adds elements to the rear of the queue, and the dequeue operation removes elements from the front of the queue.

4. **Real-Life Analogy:**
   - A common analogy is standing in line at a supermarket checkout. The first person who joins the line is the first to be served, and others follow in the order they joined.

5. **Usage in Computer Science:**
   - FIFO is widely used in various computing scenarios, such as job scheduling, task processing, and managing data in a way that respects the order of arrival.

6. **Guarantees Order:**
   - The FIFO principle guarantees that elements are processed in the order in which they were added, providing a fair and predictable way to handle tasks.

### Example of FIFO in a Queue:

Consider a simple queue with the following operations:

1. Enqueue A
2. Enqueue B
3. Enqueue C
4. Dequeue (Remove and process the front element)

The queue would look like this over time:

```
Enqueue A   -->   A
Enqueue B   -->   A, B
Enqueue C   -->   A, B, C
Dequeue     -->   B, C (A is processed and removed)
```

In this example, A, being the first element enqueued, is the first to be dequeued, following the FIFO principle.


# II. Basic Operations

## A. Enqueue (Insertion)
In Java, the `Queue` interface provides the `enqueue` operation, which is typically called `offer()` in Java. The `offer()` method is used to insert an element into the rear of the queue. Note that the `Queue` interface is part of the Java Collections Framework and has several implementations, such as `LinkedList` and `ArrayDeque`, that provide the `offer()` method.

Here's an example of how to use `offer()` for enqueue (insertion) in Java:

```java
import java.util.LinkedList;
import java.util.Queue;

public class EnqueueExample {
    public static void main(String[] args) {
        // Creating a Queue using LinkedList
        Queue<String> queue = new LinkedList<>();

        // Enqueue (Insertion) using offer() method
        queue.offer("Element 1");
        queue.offer("Element 2");
        queue.offer("Element 3");

        // Displaying the Queue after enqueue operations
        System.out.println("Queue after enqueue operations: " + queue);

        // You can continue to enqueue more elements as needed
        queue.offer("Element 4");

        // Displaying the Queue after additional enqueue operation
        System.out.println("Queue after additional enqueue: " + queue);
    }
}
```

In this example:

1. We create a `Queue` using the `LinkedList` class. Note that you can use other implementations of the `Queue` interface as well, such as `ArrayDeque`.

2. We use the `offer()` method to enqueue (insert) elements into the queue. The order in which elements are enqueued reflects the FIFO principle.

3. We print the queue to observe the changes after each enqueue operation.

Remember that the `offer()` method returns `true` if the element was successfully added to the queue and `false` otherwise (for example, if the queue has a fixed capacity and is full). It is a good practice to check the return value if necessary.

## B. Dequeue (Deletion)
In Java, the `Queue` interface provides the `dequeue` operation for removing elements, which is typically implemented as the `poll()` method. The `poll()` method removes and returns the element at the front of the queue. It follows the FIFO (First-In-First-Out) principle, meaning that the first element enqueued is the first to be dequeued.

Here's an example of how to use `poll()` for dequeue (deletion) in Java:

```java
import java.util.LinkedList;
import java.util.Queue;

public class DequeueExample {
    public static void main(String[] args) {
        // Creating a Queue using LinkedList
        Queue<String> queue = new LinkedList<>();

        // Enqueue (Insertion) using offer() method
        queue.offer("Element 1");
        queue.offer("Element 2");
        queue.offer("Element 3");

        // Displaying the Queue before dequeue operation
        System.out.println("Queue before dequeue operation: " + queue);

        // Dequeue (Deletion) using poll() method
        String removedElement = queue.poll();

        // Displaying the removed element and the Queue after dequeue operation
        System.out.println("Removed Element: " + removedElement);
        System.out.println("Queue after dequeue operation: " + queue);
    }
}
```

In this example:

1. We create a `Queue` using the `LinkedList` class.

2. We use the `offer()` method to enqueue (insert) elements into the queue.

3. We use the `poll()` method to dequeue (remove) the element from the front of the queue. The removed element is returned by the `poll()` method.

4. We print the removed element and the queue to observe the changes after the dequeue operation.

The output will show the removed element and the updated queue after the dequeue operation.

It's important to note that the `poll()` method returns `null` if the queue is empty. If you want to avoid a `null` result, you can use the `remove()` method, which throws a `NoSuchElementException` if the queue is empty. Another option is to use the `peek()` method to check the front element without removing it.

## C. Peek (Front and Rear)
In Java, the `Queue` interface provides the `peek` operation for examining the element at the front of the queue without removing it. There are two variants: `peek()` and `peekLast()`. The `peek()` method returns the element at the front of the queue, while `peekLast()` returns the element at the rear of the queue. These methods are useful when you want to inspect the elements without modifying the queue.

Here's an example demonstrating the use of `peek()` and `peekLast()`:

```java
import java.util.LinkedList;
import java.util.Queue;

public class PeekExample {
    public static void main(String[] args) {
        // Creating a Queue using LinkedList
        Queue<String> queue = new LinkedList<>();

        // Enqueue (Insertion) using offer() method
        queue.offer("Element 1");
        queue.offer("Element 2");
        queue.offer("Element 3");

        // Displaying the Queue before peek operations
        System.out.println("Queue before peek operations: " + queue);

        // Peek at the front (returns the element at the front without removing it)
        String frontElement = queue.peek();

        // Displaying the front element
        System.out.println("Front Element: " + frontElement);

        // Peek at the rear (returns the element at the rear without removing it)
        String rearElement = ((LinkedList<String>) queue).peekLast();

        // Displaying the rear element
        System.out.println("Rear Element: " + rearElement);

        // Displaying the Queue after peek operations
        System.out.println("Queue after peek operations: " + queue);
    }
}
```

In this example:

1. We create a `Queue` using the `LinkedList` class.

2. We use the `offer()` method to enqueue (insert) elements into the queue.

3. We use the `peek()` method to peek at the element at the front of the queue without removing it.

4. We use `((LinkedList<String>) queue).peekLast()` to peek at the element at the rear of the queue. Note that casting to `LinkedList` is necessary to access the `peekLast()` method.

5. We print the front and rear elements and the queue to observe the changes after the peek operations.

The output will show the front and rear elements without modifying the original queue.

It's important to note that both `peek()` and `peekLast()` return `null` if the queue is empty. Before calling these methods, you may want to check if the queue is not empty to avoid null pointer exceptions.

## D. Size and isEmpty operations
In Java, the `Queue` interface provides the `size()` and `isEmpty()` operations for determining the number of elements in the queue and checking if the queue is empty, respectively.

Here's an example demonstrating the use of `size()` and `isEmpty()`:

```java
import java.util.LinkedList;
import java.util.Queue;

public class SizeAndIsEmptyExample {
    public static void main(String[] args) {
        // Creating a Queue using LinkedList
        Queue<String> queue = new LinkedList<>();

        // Enqueue (Insertion) using offer() method
        queue.offer("Element 1");
        queue.offer("Element 2");
        queue.offer("Element 3");

        // Checking the size of the Queue
        int queueSize = queue.size();
        System.out.println("Size of the Queue: " + queueSize);

        // Checking if the Queue is empty
        boolean isQueueEmpty = queue.isEmpty();
        System.out.println("Is the Queue empty? " + isQueueEmpty);

        // Dequeue (Deletion) using poll() method
        String removedElement = queue.poll();

        // Displaying the removed element
        System.out.println("Removed Element: " + removedElement);

        // Checking the size of the Queue after dequeue operation
        queueSize = queue.size();
        System.out.println("Size of the Queue after dequeue: " + queueSize);

        // Checking if the Queue is empty after dequeue operation
        isQueueEmpty = queue.isEmpty();
        System.out.println("Is the Queue empty after dequeue? " + isQueueEmpty);
    }
}
```

In this example:

1. We create a `Queue` using the `LinkedList` class.

2. We use the `offer()` method to enqueue (insert) elements into the queue.

3. We use the `size()` method to determine the number of elements in the queue.

4. We use the `isEmpty()` method to check if the queue is empty.

5. We use the `poll()` method to dequeue (remove) an element from the front of the queue.

6. We print the size of the queue and whether it is empty before and after the dequeue operation.

The output will show the size of the queue and whether it is empty at different points in the program.

It's important to note that the `size()` method returns the number of elements in the queue, and the `isEmpty()` method returns `true` if the queue is empty and `false` otherwise. These methods are helpful for making decisions based on the current state of the queue.

# III. Types of Queues
## A. Linear Queue
A linear queue is a type of queue in which elements are arranged in a linear or sequential manner. It follows the First-In-First-Out (FIFO) principle, where the first element inserted is the first one to be removed. In a linear queue, elements are enqueued (inserted) at the rear and dequeued (removed) from the front.

Here's a basic overview of operations and characteristics of a linear queue:

### Operations on Linear Queue:

1. **Enqueue (Insertion):**
   - Adds an element to the rear of the queue.

2. **Dequeue (Deletion):**
   - Removes the element from the front of the queue.

3. **Peek (Front):**
   - Views the element at the front of the queue without removing it.

4. **isEmpty:**
   - Checks if the queue is empty.

5. **isFull:**
   - Checks if the queue is full (applicable in bounded or fixed-size queues).

### Characteristics of Linear Queue:

1. **Linear Structure:**
   - Elements are stored in a linear or sequential order.

2. **Fixed Size (Optional):**
   - Linear queues can be of fixed size (bounded) or dynamic size (unbounded).

3. **Front and Rear Pointers:**
   - Front and rear pointers keep track of the positions for enqueue and dequeue operations.

4. **FIFO Principle:**
   - Follows the First-In-First-Out order, ensuring that the first element inserted is the first one to be removed.

5. **Dynamic Size (Unbounded):**
   - In an unbounded linear queue, the size can dynamically grow as elements are enqueued.

### Implementation Example in Java:

Here's a basic example of implementing a linear queue using an array in Java:

```java
public class LinearQueue {
    private static final int MAX_SIZE = 10;
    private int[] queueArray;
    private int front, rear;

    public LinearQueue() {
        this.queueArray = new int[MAX_SIZE];
        this.front = -1;
        this.rear = -1;
    }

    public void enqueue(int item) {
        if (rear == MAX_SIZE - 1) {
            System.out.println("Queue is full. Cannot enqueue.");
        } else {
            if (front == -1) {
                front = 0;
            }
            queueArray[++rear] = item;
            System.out.println("Enqueued: " + item);
        }
    }

    public void dequeue() {
        if (front == -1) {
            System.out.println("Queue is empty. Cannot dequeue.");
        } else {
            int dequeuedItem = queueArray[front++];
            System.out.println("Dequeued: " + dequeuedItem);
            if (front > rear) {
                // Reset pointers when the last element is dequeued
                front = -1;
                rear = -1;
            }
        }
    }

    public void display() {
        if (front == -1) {
            System.out.println("Queue is empty.");
        } else {
            System.out.print("Queue: ");
            for (int i = front; i <= rear; i++) {
                System.out.print(queueArray[i] + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        LinearQueue queue = new LinearQueue();

        queue.enqueue(10);
        queue.enqueue(20);
        queue.enqueue(30);

        queue.display();

        queue.dequeue();
        queue.display();

        queue.dequeue();
        queue.display();

        queue.dequeue();
        queue.display();
    }
}
```

This Java example demonstrates a simple linear queue implemented using an array. It includes basic enqueue, dequeue, and display operations. Keep in mind that this is a basic example, and in real-world scenarios, you might want to consider using dynamic data structures like linked lists for an unbounded linear queue.

## B. Circular Queue
A circular queue is a variation of a linear queue with a circular structure. In a circular queue, the rear and front pointers wrap around the ends of the queue, forming a circle. This circular arrangement allows efficient use of space and avoids the need to shift elements when the front pointer reaches the end of the queue.

Here's an overview of the operations and characteristics of a circular queue:

### Operations on Circular Queue:

1. **Enqueue (Insertion):**
   - Adds an element to the rear of the queue.

2. **Dequeue (Deletion):**
   - Removes the element from the front of the queue.

3. **Peek (Front):**
   - Views the element at the front of the queue without removing it.

4. **isFull:**
   - Checks if the queue is full (applicable in bounded or fixed-size circular queues).

5. **isEmpty:**
   - Checks if the queue is empty.

### Characteristics of Circular Queue:

1. **Circular Structure:**
   - Elements are stored in a circular or looped order.

2. **Fixed Size (Optional):**
   - Circular queues can be of fixed size (bounded) or dynamic size (unbounded).

3. **Front and Rear Pointers:**
   - Front and rear pointers wrap around the ends of the queue.

4. **Efficient Use of Space:**
   - The circular structure avoids the need to shift elements when the front pointer reaches the end.

5. **FIFO Principle:**
   - Follows the First-In-First-Out order, ensuring that the first element inserted is the first one to be removed.

### Implementation Example in Java:

Here's a basic example of implementing a circular queue using an array in Java:

```java
public class CircularQueue {
    private static final int MAX_SIZE = 5;
    private int[] queueArray;
    private int front, rear;

    public CircularQueue() {
        this.queueArray = new int[MAX_SIZE];
        this.front = -1;
        this.rear = -1;
    }

    public void enqueue(int item) {
        if ((rear + 1) % MAX_SIZE == front) {
            System.out.println("Queue is full. Cannot enqueue.");
        } else {
            if (front == -1) {
                front = 0;
            }
            rear = (rear + 1) % MAX_SIZE;
            queueArray[rear] = item;
            System.out.println("Enqueued: " + item);
        }
    }

    public void dequeue() {
        if (front == -1) {
            System.out.println("Queue is empty. Cannot dequeue.");
        } else {
            int dequeuedItem = queueArray[front];
            System.out.println("Dequeued: " + dequeuedItem);
            if (front == rear) {
                // Reset pointers when the last element is dequeued
                front = -1;
                rear = -1;
            } else {
                front = (front + 1) % MAX_SIZE;
            }
        }
    }

    public void display() {
        if (front == -1) {
            System.out.println("Queue is empty.");
        } else {
            System.out.print("Queue: ");
            int i = front;
            do {
                System.out.print(queueArray[i] + " ");
                i = (i + 1) % MAX_SIZE;
            } while (i != (rear + 1) % MAX_SIZE);
            System.out.println();
        }
    }

    public static void main(String[] args) {
        CircularQueue circularQueue = new CircularQueue();

        circularQueue.enqueue(10);
        circularQueue.enqueue(20);
        circularQueue.enqueue(30);

        circularQueue.display();

        circularQueue.dequeue();
        circularQueue.display();

        circularQueue.enqueue(40);
        circularQueue.enqueue(50);

        circularQueue.display();
    }
}
```

This Java example demonstrates a simple circular queue implemented using an array. It includes basic enqueue, dequeue, and display operations. The circular nature of the queue is evident in the wrap-around logic used for the front and rear pointers. As with the linear queue, in real-world scenarios, you might want to consider using dynamic data structures like linked lists for an unbounded circular queue.

## C. Priority Queue
A priority queue is a data structure that stores elements with associated priorities. The elements are dequeued in order of their priorities, rather than in a strictly first-in-first-out (FIFO) or last-in-first-out (LIFO) order. The element with the highest (or lowest, depending on the implementation) priority is dequeued first.

Here are the key characteristics and operations of a priority queue:

### Characteristics of Priority Queue:

1. **Priority-Based Order:**
   - Elements are organized based on their priorities.

2. **Not Strictly FIFO or LIFO:**
   - Unlike standard queues or stacks, the priority queue does not strictly follow FIFO or LIFO principles.

3. **Highest or Lowest Priority:**
   - The element with the highest (or lowest) priority is dequeued first.

4. **Dynamic Size:**
   - Priority queues can dynamically grow or shrink based on the number of elements and their priorities.

### Operations on Priority Queue:

1. **Enqueue (Insertion):**
   - Adds an element with its associated priority to the priority queue.

2. **Dequeue (Removal):**
   - Removes the element with the highest (or lowest) priority from the priority queue.

3. **Peek (Front):**
   - Views the element with the highest (or lowest) priority without removing it.

4. **Size and isEmpty:**
   - Checks the number of elements in the priority queue and whether it is empty.

### Implementation Example in Java:

Java provides the `PriorityQueue` class in the `java.util` package, which implements a priority queue based on a priority heap. Here's a basic example:

```java
import java.util.PriorityQueue;

public class PriorityQueueExample {
    public static void main(String[] args) {
        // Creating a Priority Queue
        PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();

        // Enqueue (Insertion) with priorities
        priorityQueue.offer(30);
        priorityQueue.offer(20);
        priorityQueue.offer(50);
        priorityQueue.offer(10);

        // Displaying the Priority Queue
        System.out.println("Priority Queue: " + priorityQueue);

        // Dequeue (Removal) - Removes the element with the highest priority
        int dequeuedElement = priorityQueue.poll();
        System.out.println("Dequeued Element: " + dequeuedElement);

        // Peek (Front) - Views the element with the highest priority without removing it
        int peekedElement = priorityQueue.peek();
        System.out.println("Peeked Element: " + peekedElement);

        // Displaying the Priority Queue after dequeue and peek operations
        System.out.println("Priority Queue after operations: " + priorityQueue);
    }
}
```

In this example:

1. We create a `PriorityQueue` and use the `offer()` method to enqueue elements with associated priorities.

2. The `poll()` method is used to dequeue (remove) the element with the highest priority.

3. The `peek()` method is used to view the element with the highest priority without removing it.

4. The output demonstrates the priority queue after the enqueue, dequeue, and peek operations.

The `PriorityQueue` class in Java uses a min-heap by default, meaning that the smallest element has the highest priority. You can also create a max-heap by providing a custom comparator during the creation of the `PriorityQueue`.

## D. Double-Ended Queue (Deque)
A Double-Ended Queue, often abbreviated as Deque, is a data structure that allows insertion and deletion of elements from both ends – the front and the rear. It combines the features of both stacks and queues, providing versatility in managing elements.

Here are the key characteristics and operations of a Double-Ended Queue (Deque):

### Characteristics of Deque:

1. **Front and Rear Operations:**
   - Elements can be inserted or removed from both the front and the rear.

2. **Versatility:**
   - Deques can function as both queues and stacks, offering flexibility in managing elements.

3. **Dynamic Size:**
   - Deques can dynamically grow or shrink based on the number of elements.

4. **Linear Structure:**
   - Elements are arranged in a linear or sequential order.

### Operations on Deque:

1. **Insertion at Front (`offerFirst()` or `addFirst()`):**
   - Adds an element to the front of the deque.

2. **Insertion at Rear (`offerLast()` or `addLast()`):**
   - Adds an element to the rear of the deque.

3. **Deletion from Front (`pollFirst()` or `removeFirst()`):**
   - Removes and returns the element from the front of the deque.

4. **Deletion from Rear (`pollLast()` or `removeLast()`):**
   - Removes and returns the element from the rear of the deque.

5. **Peek at Front (`peekFirst()` or `getFirst()`):**
   - Views the element at the front of the deque without removing it.

6. **Peek at Rear (`peekLast()` or `getLast()`):**
   - Views the element at the rear of the deque without removing it.

7. **Size and isEmpty:**
   - Checks the number of elements in the deque and whether it is empty.

### Implementation Example in Java:

Java provides the `Deque` interface in the `java.util` package, and one of its common implementations is `LinkedList`. Here's a basic example:

```java
import java.util.LinkedList;
import java.util.Deque;

public class DequeExample {
    public static void main(String[] args) {
        // Creating a Deque using LinkedList
        Deque<String> deque = new LinkedList<>();

        // Insertion at Front
        deque.addFirst("Front Element 1");
        deque.offerFirst("Front Element 2");

        // Insertion at Rear
        deque.addLast("Rear Element 1");
        deque.offerLast("Rear Element 2");

        // Displaying the Deque
        System.out.println("Deque: " + deque);

        // Deletion from Front
        String removedFromFront = deque.pollFirst();
        System.out.println("Removed from Front: " + removedFromFront);

        // Deletion from Rear
        String removedFromRear = deque.pollLast();
        System.out.println("Removed from Rear: " + removedFromRear);

        // Displaying the Deque after deletions
        System.out.println("Deque after deletions: " + deque);
    }
}
```

In this example:

1. We create a `Deque` using the `LinkedList` class.

2. We use various methods such as `addFirst()`, `offerFirst()`, `addLast()`, and `offerLast()` to insert elements at both the front and the rear.

3. The `pollFirst()` and `pollLast()` methods are used to remove and return elements from the front and the rear, respectively.

4. The output demonstrates the deque after insertion and deletion operations.

This Deque implementation provides a powerful and flexible way to manage elements in both LIFO and FIFO manners.

# IV. Implementations
## A. Linked List-based Queue
A linked list-based queue is a type of queue data structure that is implemented using a linked list. In this structure, elements are stored in nodes, and each node points to the next node in the sequence. The front and rear of the queue are maintained by pointers to the first and last nodes, respectively.

Here's a basic overview of the characteristics and operations of a linked list-based queue:

### Characteristics of Linked List-Based Queue:

1. **Dynamic Size:**
   - The linked list-based queue can dynamically grow or shrink based on the number of elements.

2. **Front and Rear Pointers:**
   - Front and rear pointers keep track of the positions for enqueue and dequeue operations.

3. **Linear Structure:**
   - Elements are stored in a linked list, and the order of insertion is maintained.

4. **FIFO Principle:**
   - Follows the First-In-First-Out order, ensuring that the first element inserted is the first one to be removed.

### Operations on Linked List-Based Queue:

1. **Enqueue (Insertion):**
   - Adds an element to the rear of the queue by inserting a node at the end of the linked list.

2. **Dequeue (Deletion):**
   - Removes the element from the front of the queue by deleting the first node in the linked list.

3. **Peek (Front):**
   - Views the element at the front of the queue without removing it.

4. **Size and isEmpty:**
   - Checks the number of elements in the queue and whether it is empty.

### Implementation Example in Java:

Here's a basic example of implementing a linked list-based queue in Java:

```java
class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedListQueue {
    private Node front, rear;

    public LinkedListQueue() {
        this.front = null;
        this.rear = null;
    }

    public void enqueue(int item) {
        Node newNode = new Node(item);
        if (rear == null) {
            // If the queue is empty, set both front and rear to the new node
            front = newNode;
            rear = newNode;
        } else {
            // Otherwise, add the new node to the end and update rear
            rear.next = newNode;
            rear = newNode;
        }
        System.out.println("Enqueued: " + item);
    }

    public void dequeue() {
        if (front == null) {
            System.out.println("Queue is empty. Cannot dequeue.");
        } else {
            // Remove the front node and update front
            int dequeuedItem = front.data;
            front = front.next;
            System.out.println("Dequeued: " + dequeuedItem);

            // If the queue becomes empty, update rear to null as well
            if (front == null) {
                rear = null;
            }
        }
    }

    public void display() {
        if (front == null) {
            System.out.println("Queue is empty.");
        } else {
            System.out.print("Queue: ");
            Node current = front;
            while (current != null) {
                System.out.print(current.data + " ");
                current = current.next;
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        LinkedListQueue linkedListQueue = new LinkedListQueue();

        linkedListQueue.enqueue(10);
        linkedListQueue.enqueue(20);
        linkedListQueue.enqueue(30);

        linkedListQueue.display();

        linkedListQueue.dequeue();
        linkedListQueue.display();

        linkedListQueue.enqueue(40);
        linkedListQueue.enqueue(50);

        linkedListQueue.display();
    }
}
```

In this example:

1. We define a `Node` class to represent elements in the linked list.

2. We create a linked list-based queue with front and rear pointers.

3. The `enqueue` method inserts a new node at the rear of the linked list.

4. The `dequeue` method removes the front node from the linked list.

5. The `display` method shows the current state of the queue after various operations.

# V. Applications
## A. Job Scheduling
Job scheduling is a critical aspect in various computing and operating system environments. Circular queues, or queues in general, are commonly used in job scheduling due to their ability to follow the First-In-First-Out (FIFO) principle. Here's how circular queues can be applied in job scheduling:

1. **Print Queue:**
   - In a network or office environment with multiple users printing documents, a circular queue can be used as a print queue. Print jobs are added to the queue as users submit print requests. The printer processes the jobs in the order they were submitted, ensuring fairness through the FIFO principle.

2. **Batch Processing Systems:**
   - In batch processing systems, where multiple jobs are executed in batches, circular queues help manage the order of job execution. Each batch of jobs is added to the queue, and the system processes them sequentially. This ensures that the jobs are executed in the order they were submitted.

3. **Task Scheduling in Operating Systems:**
   - Operating systems often use circular queues for scheduling tasks and processes. The ready queue maintains a list of tasks that are ready to be executed by the CPU. The scheduler selects tasks from the front of the queue based on their priority or other scheduling algorithms.

4. **Network Data Packet Queues:**
   - In networking, circular queues are used to manage the flow of data packets. Incoming data packets are added to the rear of the queue, and the network device processes them in the order they arrive. This ensures a fair and orderly processing of data.

5. **Multi-User Environments:**
   - In multi-user systems, circular queues are employed for managing user requests or commands. For example, in a command-line interface, user commands are added to a circular queue, and the system processes them in the order they were entered.

6. **Task Scheduling in Real-Time Systems:**
   - Real-time systems often use circular queues for scheduling tasks with specific deadlines. Tasks are enqueued based on their priority and deadline, and the system ensures that tasks are executed in a timely manner.

7. **Buffer Management in I/O Systems:**
   - Circular queues are used to manage buffers in input/output (I/O) systems. Data is enqueued in the buffer, and the system processes and dequeues the data to ensure a smooth flow of information between the I/O devices and the main processing unit.
## B. Print Queue
A print queue is an essential component in computer systems that manages the order in which print jobs are processed by a printer. It serves as an intermediary between users and the printer, ensuring that multiple print requests are handled efficiently and in a systematic manner. Here are some applications and benefits of a print queue:

1. **Orderly Print Processing:**
   - A print queue ensures that print jobs are processed in the order they are received. This helps in maintaining a fair and organized system, preventing conflicts when multiple users submit print requests.

2. **Print Job Prioritization:**
   - Print queues often allow for prioritization of print jobs. Higher-priority jobs, such as urgent or important documents, can be given precedence over lower-priority jobs in the queue.

3. **Resource Management:**
   - Print queues help in managing printer resources effectively. By processing print jobs in an orderly fashion, it prevents the printer from being overwhelmed and ensures optimal resource utilization.

4. **Queue Monitoring and Management:**
   - Administrators can monitor the print queue to check the status of print jobs, identify any issues, and manage the print queue, such as canceling or pausing specific print jobs.

5. **Centralized Printing Control:**
   - In networked environments, print queues offer centralized control over printing activities. Print jobs from multiple users across the network can be managed from a central location, providing administrators with control and oversight.

6. **Print Job Logging:**
   - Print queues often log details of print jobs, such as user, document name, and time of submission. This logging can be useful for tracking usage patterns, diagnosing issues, and generating reports.

7. **Print Job Scheduling:**
   - Print queues may support scheduling options, allowing users to specify when their print jobs should be processed. This is helpful for managing printer usage during peak and off-peak hours.

8. **Error Handling:**
   - If there is an issue with a print job or the printer encounters an error, the print queue can handle the situation by notifying the user, logging the error, or automatically retrying the print job.

9. **Print Server Functionality:**
   - In networked environments, a print queue is often associated with a print server. The print server manages the print queue and handles communication between client devices and the printer.

10. **Remote Printing:**
    - Print queues enable remote printing, allowing users to submit print jobs from their devices to a printer located elsewhere on the network. This is especially useful in large organizations with distributed printer locations.
## C. Breadth-First Search (BFS) in Graphs
Breadth-First Search (BFS) is a graph traversal algorithm that explores all the vertices of a graph in breadth-first order, i.e., it visits all the vertices at the same level before moving on to the next level. BFS is often used in various applications, and one of the significant applications is in graph traversal. Here's how BFS can be applied to graph traversal:

### Application: Breadth-First Search in Graph Traversal

1. **Shortest Path and Minimum Spanning Tree:**
   - BFS can be used to find the shortest path from a source vertex to all other vertices in an unweighted graph. It is also used to find the minimum spanning tree in an unweighted graph.

2. **Connected Components:**
   - BFS can be used to find connected components in an undirected graph. It helps identify groups of vertices that are connected to each other.

3. **Web Crawlers:**
   - BFS is employed by web crawlers to index and discover web pages on the internet. Starting from a seed URL, BFS explores web pages layer by layer.

4. **Social Network Analysis:**
   - BFS can be applied to analyze social networks, identifying clusters of friends or connections within a social graph.

5. **Puzzle Solving:**
   - BFS is used in solving puzzles where each state is represented as a vertex, and transitions between states are represented as edges. Examples include the sliding puzzle or the 8-puzzle problem.

6. **Garbage Collection:**
   - In systems programming, BFS is used for garbage collection algorithms to identify and reclaim memory that is no longer in use.

7. **Network Broadcasting:**
   - BFS is used in network broadcasting to broadcast messages to all nodes in a network.

### Example Code in Java:

Here's a simple Java code snippet demonstrating BFS in graph traversal:

```java
import java.util.LinkedList;
import java.util.Queue;

public class GraphTraversalBFS {
    static class Graph {
        private int V; // Number of vertices
        private LinkedList<Integer>[] adjList; // Adjacency list

        public Graph(int v) {
            this.V = v;
            adjList = new LinkedList[v];
            for (int i = 0; i < v; ++i) {
                adjList[i] = new LinkedList<>();
            }
        }

        // Add an edge to the graph
        void addEdge(int v, int w) {
            adjList[v].add(w);
        }

        // BFS traversal starting from a given source vertex
        void BFS(int s) {
            boolean[] visited = new boolean[V];
            Queue<Integer> queue = new LinkedList<>();

            visited[s] = true;
            queue.add(s);

            while (!queue.isEmpty()) {
                s = queue.poll();
                System.out.print(s + " ");

                for (int neighbor : adjList[s]) {
                    if (!visited[neighbor]) {
                        visited[neighbor] = true;
                        queue.add(neighbor);
                    }
                }
            }
        }
    }

    public static void main(String[] args) {
        Graph graph = new Graph(6);

        // Adding edges to the graph
        graph.addEdge(0, 1);
        graph.addEdge(0, 2);
        graph.addEdge(1, 3);
        graph.addEdge(1, 4);
        graph.addEdge(2, 4);
        graph.addEdge(3, 4);
        graph.addEdge(3, 5);

        System.out.println("BFS traversal starting from vertex 0:");
        graph.BFS(0);
    }
}
```

In this example:

- We represent the graph using an adjacency list.
- The `BFS` method performs BFS traversal starting from a given source vertex.
- The output shows the BFS traversal order starting from vertex 0.
## D. Task Scheduling in Operating Systems
Task scheduling is a critical aspect of operating systems, and circular queues are often employed in this context for managing the execution of tasks. Circular queues provide an efficient way to organize and cycle through tasks in a repeated fashion. Here are some aspects of task scheduling in operating systems where circular queues are commonly used:

1. **Round Robin Scheduling:**
   - **Definition:** In round robin scheduling, each task is assigned a fixed time slot or quantum for execution. When a task's time quantum expires, it is moved to the back of the queue, and the next task in line gets the CPU.
   - **Circular Queue Usage:** A circular queue is a natural fit for implementing round robin scheduling. The front of the queue represents the task currently using the CPU, and when its time quantum expires, it is moved to the rear of the queue.

2. **Multilevel Queue Scheduling:**
   - **Definition:** In multilevel queue scheduling, tasks are divided into multiple queues based on priority. Each queue has its own scheduling algorithm. Tasks move between queues based on their behavior and priority.
   - **Circular Queue Usage:** Circular queues are often used to implement each priority level queue. Tasks in a particular priority level are arranged in a circular queue, and scheduling policies, such as round robin, can be applied within each priority queue.

3. **Real-Time Systems:**
   - **Definition:** Real-time operating systems require tasks to meet strict timing constraints. Tasks are scheduled based on deadlines to ensure that critical tasks are executed in a timely manner.
   - **Circular Queue Usage:** Circular queues can be used to manage tasks with deadlines. Tasks are arranged in a circular queue based on their deadlines, and the scheduler ensures that tasks are executed in the order of their deadlines.

4. **Event-driven Systems:**
   - **Definition:** Operating systems for embedded systems or applications that respond to events often use an event-driven model. Tasks are triggered by specific events and are scheduled accordingly.
   - **Circular Queue Usage:** Circular queues can be used to manage tasks associated with different events. When an event occurs, the corresponding task is enqueued and executed when it reaches the front of the circular queue.

5. **Periodic Task Execution:**
   - **Definition:** In certain applications, tasks need to be executed periodically at fixed intervals. This is common in systems dealing with periodic data acquisition, communication, or control.
   - **Circular Queue Usage:** Tasks with periodic execution requirements can be organized in a circular queue. The queue ensures that tasks are executed in a cyclical manner, meeting their specified periodicity.

# VI. Advanced Concepts
## A. Queues in Multithreading
Queues play a crucial role in multithreading applications by providing a mechanism for communication and synchronization between threads. In multithreading, threads often need to communicate with each other or coordinate their activities. Queues, specifically blocking queues, are commonly used for this purpose. Here's an overview of using queues in multithreading along with examples:

### 1. **BlockingQueue Interface:**
Java provides the `BlockingQueue` interface in the `java.util.concurrent` package, which is designed for use in multithreaded environments. It extends the `Queue` interface and includes methods that support operations that wait for the queue to become non-empty when retrieving an element or become non-full when storing an element.

### 2. **Example of Producer-Consumer Pattern:**
One common use case for queues in multithreading is implementing the producer-consumer pattern. In this pattern, one or more producer threads produce data, and one or more consumer threads consume the data. A blocking queue serves as the shared buffer between producers and consumers.

Here's an example in Java using `LinkedBlockingQueue`:

```java
import java.util.concurrent.BlockingQueue;
import java.util.concurrent.LinkedBlockingQueue;

class Producer implements Runnable {
    private BlockingQueue<Integer> queue;

    public Producer(BlockingQueue<Integer> queue) {
        this.queue = queue;
    }

    @Override
    public void run() {
        try {
            for (int i = 1; i <= 5; i++) {
                System.out.println("Producing: " + i);
                queue.put(i); // Inserts the specified element into this queue
                Thread.sleep(1000);
            }
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}

class Consumer implements Runnable {
    private BlockingQueue<Integer> queue;

    public Consumer(BlockingQueue<Integer> queue) {
        this.queue = queue;
    }

    @Override
    public void run() {
        try {
            while (true) {
                int value = queue.take(); // Retrieves and removes the head of this queue
                System.out.println("Consuming: " + value);
                Thread.sleep(2000);
            }
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}

public class ProducerConsumerExample {
    public static void main(String[] args) {
        BlockingQueue<Integer> queue = new LinkedBlockingQueue<>(3);

        Thread producerThread = new Thread(new Producer(queue));
        Thread consumerThread = new Thread(new Consumer(queue));

        producerThread.start();
        consumerThread.start();
    }
}
```

In this example:

- The `LinkedBlockingQueue` is used as the shared buffer between the producer and consumer threads.
- The `Producer` class produces integers and puts them into the queue using the `put` method.
- The `Consumer` class takes integers from the queue using the `take` method.
- The producer and consumer threads run concurrently, demonstrating the producer-consumer pattern.

### 3. **Other BlockingQueue Implementations:**
Java provides various implementations of the `BlockingQueue` interface, including `ArrayBlockingQueue`, `PriorityBlockingQueue`, and `DelayQueue`. The choice of implementation depends on specific requirements and characteristics of the application.

Using queues in multithreading ensures proper synchronization between threads, preventing race conditions and improving the overall performance of concurrent applications.

## B. Blocking Queues
Blocking queues are a type of data structure commonly used in concurrent programming and multithreading to facilitate communication and coordination between threads. These queues provide blocking operations for adding and removing elements, meaning that if a thread attempts to dequeue an element from an empty queue or enqueue an element into a full queue, it will be blocked until the operation can be completed.

Java's `BlockingQueue` interface, available in the `java.util.concurrent` package, defines a set of methods that support blocking operations for adding, removing, and inspecting elements in a queue. Some commonly used blocking queue implementations in Java include `LinkedBlockingQueue`, `ArrayBlockingQueue`, and `PriorityBlockingQueue`.

Here's a brief overview of the key features of blocking queues:

### Key Features:

1. **Blocking Operations:**
   - Blocking queues support blocking operations for both enqueueing (putting) and dequeueing (taking) elements. If the queue is full, an attempt to enqueue will block until space becomes available. If the queue is empty, an attempt to dequeue will block until an element is available.

2. **Thread Safety:**
   - Blocking queues are designed to be thread-safe, making them suitable for concurrent environments. They handle synchronization and coordination between threads internally.

3. **FIFO Order:**
   - Like regular queues, blocking queues maintain the First-In-First-Out (FIFO) order, ensuring that the order of elements is preserved.

4. **Dynamic Size:**
   - Blocking queues can dynamically grow or shrink based on the number of elements.

### Example of Using a Blocking Queue in Java:

Here's an example using `LinkedBlockingQueue`:

```java
import java.util.concurrent.BlockingQueue;
import java.util.concurrent.LinkedBlockingQueue;

public class BlockingQueueExample {
    public static void main(String[] args) {
        // Creating a LinkedBlockingQueue with a maximum capacity of 3
        BlockingQueue<Integer> blockingQueue = new LinkedBlockingQueue<>(3);

        // Producer thread
        Thread producer = new Thread(() -> {
            try {
                for (int i = 1; i <= 5; i++) {
                    blockingQueue.put(i); // Enqueue (put) operation
                    System.out.println("Produced: " + i);
                }
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        });

        // Consumer thread
        Thread consumer = new Thread(() -> {
            try {
                for (int i = 1; i <= 5; i++) {
                    int value = blockingQueue.take(); // Dequeue (take) operation
                    System.out.println("Consumed: " + value);
                }
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        });

        // Starting producer and consumer threads
        producer.start();
        consumer.start();
    }
}
```

In this example:

- The `LinkedBlockingQueue` is created with a maximum capacity of 3.
- The producer thread enqueues elements using the `put` method.
- The consumer thread dequeues elements using the `take` method.
- The producer and consumer threads run concurrently, demonstrating the blocking behavior of the queue.

Blocking queues are especially useful in scenarios where threads need to communicate, synchronize, or exchange data in a producer-consumer pattern. They provide an effective way to handle coordination and synchronization between threads in a multithreaded environment.