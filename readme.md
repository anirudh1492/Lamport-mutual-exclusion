# CS/CE/TE 6378: Project I

## Instructor: Ravi Prakash

This is an individual project and you are required to demonstrate its operation to the instructor and/or the TA to
get credit for the project.

## 1 Requirements

1. Source code must be in the C /C++ /Java programming language.
2. The program must run on UTD lab machines (dc01, dc02, ..., dc45).

## 2 Client-Server Model

In this project, you are expected to useclient-servermodel of computing. You will need to know thread and/or socket
programming and its APIs for the language you choose. It can be assumed that each process (server/client) is running
on a single machine (dcXY). Please get familiar with basic UNIX commands to run your program ondcXY.

## 3 Description

Design and implement a distributed system which consists ofthreeserver processes andfiveclient processes. Assume
that each file is replicated on all the servers, and all replicas of a file are consistent in the beginning. A client can
perform a READ or WRITE operation on the files. READ operation involves only one server that has the target file
and the server is chosen randomly by a client. WRITE involves all servers that have a copy of the target file and all
of them should be updated in order to keep the replicas consistent. READ/WRITE on a file can be performed by only
one client at a time. However, different clients are allowed to concurrently perform a READ/WRITE on different files.
In order to ensure this, implement Lamport’s mutual exclusion algorithm among clients so that no READ/WRITE
violation could occur. The operations on files (hosted by servers) can be seen ascritical sectionexecutions.
To host files, create separate directory for each server. The servers must support following operations and reply to
the clients with appropriate messages –

1. ENQUIRY : A request from a client for information about the list of hosted files.
2. READ: A request to read last line from a given file.
3. WRITE: A request to append a string to a given file.

The set of files does not change during your program’s execution. Also, assume that there is no server failure during
your program’s execution.



```
The clients must be able to do the following –
```
1. Gather information about the hosted files by querying the servers and keep the metadata for future.
2. Append a string< clientid, T imestamp >to a file,fiduring WRITE. Hereclientidis the name of the
    client, andT imestampis the value of the client’s local clock when the write request is generated. This must be
    done to all replicas offi.
3. Read last line of a file,fi, during READ.

Instead of submitting READ/WRITE requests through a command line interface, write an application that periodically
generates READ/WRITE requests for a randomly chosen file from the set of files stored by the servers.
Pertaining to socket programming, close all open sockets when your program exits/terminates. This may save you
some valuable time during the test runs and more importantly, from a panic situation during the project demonstration.
Displaying appropriate log messages to the console or to a file is very important for testing, debugging and ana-
lyzing the correctness of your program.


```
NOTE: Do not submit unnecessary files.
```

## 4 How to Run the Project
```
Assume the ip address of the machines starts from dc01 dc01.utdallas.edu to dc45.utdallas.edu
```
The ips address from client1 to client2 is:
dc01.utdallas.edu

dc02.utdallas.edu

dc03.utdallas.edu

dc04.utdallas.edu

dc05.utdallas.edu


The ips address from server1 to server3 is:

dc06.utdallas.edu

dc07.utdallas.edu

dc08.utdallas.edu

1. All servers must be started before the clients, use java -jar <file name>.jar to run 3 servers on

dc06.utdallas.edu

dc07.utdallas.edu

dc08.utdallas.edu

These 3 machines. And each server should contain 3 folders which are used to store the server files.
The root directory of these 3 folders should be the same as the server jar files. But the name of different text files 
inside the folder does not matter.

2. Then use java -jar <file name>.jar to run 5 clients at 

dc01.utdallas.edu

dc02.utdallas.edu

dc03.utdallas.edu

dc04.utdallas.edu

dc05.utdallas.edu

These 5 machines.


