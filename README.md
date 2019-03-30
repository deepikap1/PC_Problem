# PC_Problem

# Problem: 
To make sure that the producer won’t try to add data into the buffer if it’s full and that the consumer won’t try to remove data from an empty buffer.

# Solution: 
The producer is to either go to sleep or discard data if the buffer is full. The next time the consumer removes an item from the buffer, it notifies the producer, who starts to fill the buffer again. In the same way, the consumer can go to sleep if it finds the buffer to be empty. The next time the producer puts data into the buffer, it wakes up the sleeping consumer.

# The solution consists of four classes:
Q: the queue that you’re trying to synchronize
Producer: the threaded object that is producing queue entries
Consumer: the threaded object that is consuming queue entries
PC: the driver class that creates a single Q, Producer, and Consumer.

The sequencing of put() and get() call is handled by two semaphores: semProd and semCon.
1.Before put( ) can produce an item, it must acquire a permit from semProd. After it has produced the item, it releases semCon.
2.Before get( ) can consume an item, it must acquire a permit from semCon. After it consumes the item, it releases semProd.
3.This “give and take” mechanism ensures that each call to put( ) must be followed by a call to get( ).
4.Also, notice that semCon is initialized with no available permits. This ensures that put( ) executes first. The ability to set the initial synchronization state is one of the more powerful aspects of a semaphore.


# To compile the file, open your terminal and type
javac filename.java

# To run the generated class file, use
 java filename


