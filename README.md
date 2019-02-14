# EC500_HeartMonitor Exercise 1

## Architecture diagram

![Alt text](/heart_monitor/diagram.png?raw=true "diagram")

## Explanation of Architecture

Our heartmonitor design architecutre is using pyhton threads and multiprocessing. The overall architecture is semi asynchronous because we do not use blocking, but we use the threading. First, we have the random data sets in text file that has about 1000 records of heart rate, blood pressure, and oxygen saturation. We have class file called "sensors", and each method in the class will read the text file and stores each data in to the data Queue. Once sensor reads the records, also after reading, it pass each data to the "realtime data processor" class. In realtime data processor, it checks if the data seems dangerous to the patient or not. If it recognizes some of the abnormal data set, it calls the "notification manager" and "notification sender". Therefore, on the command line, the sentence appears, "Call the Nancy" or "Emergency". Depends on how serious the patient is the method of sending notification also differs which is managed by "notification manager". The SMS would be most serious, and email would be the least serious circumstance. 


## Pros and Cons 

Pros: The architecture is designed in modular based so that it is easy to add new function or class. Overall, the implementation can be easily done because each classes and methods are clearly divided and and integrated efficiently by importing from the other file. 

Cons: Since it is multi-threading when the user gets notification, it gets multiple without pause. Unless the program quit, it is hard to stop the certain method/thread. Also, there is no blocking on the data queuethat all the methods continuously running for each data set, and troubles the notification.


## What could be improved?

Adding blocking would make user much more comfortable and less annoyed. Once the notification sent, we could implement stopping function and quit the program automatically or pausing it. This way, the program could run more completed asynchronous way.
