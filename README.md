# PC_Problem

Problem: 
To make sure that the producer won’t try to add data into the buffer if it’s full and that the consumer won’t try to remove data from an empty buffer.

Solution: 
The producer is to either go to sleep or discard data if the buffer is full. The next time the consumer removes an item from the buffer, it notifies the producer, who starts to fill the buffer again. In the same way, the consumer can go to sleep if it finds the buffer to be empty. The next time the producer puts data into the buffer, it wakes up the sleeping consumer.

The solution consists of four classes:
Q: the queue that you’re trying to synchronize
Producer: the threaded object that is producing queue entries
Consumer: the threaded object that is consuming queue entries
PC: the driver class that creates a single Q, Producer, and Consumer.

The sequencing of put() and get() call is handled by two semaphores: semProd and semCon.


