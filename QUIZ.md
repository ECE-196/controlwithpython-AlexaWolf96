### How does the DevBoard handle received serial messages? How does this differ from the naïve approach?

It uses interrupt driven methods, this means it responds to external events like the serial message incoming. When a byte arrives at the serial port, it makes an interrupt
request temporarily suspending the microcontrollers current task, this allows it to perform other requests and saves power.
The naive approach makes the microcontroller continously poll the serial port to check for incoming bytes, this requires constant CPU attention wasting power. 

### What does `detached_callback` do? What would happen if it wasn't used?
It is a callback mechanism for managing asynchronous tasks or events that can execute independently from the main program. If it weren't used, then the tasks would have to be ran sequentially which could block, delay, freeze, or make it harder for the CPU to manage.

### What does `LockedSerial` do? Why is it _necessary_?
It is a multithreaded application were multiple threads can be accessed amoung shared resources asynchronously, it stops data curruption, race conditions, and other synchronization issues. It is necessary for embedded systems so multiple threads can communicate with multiple applications or devices without curruption and other issues.