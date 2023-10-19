# EX.7-IMPLEMENTATION-OF-SYSTEM-CALLS-READ-WRITE-FORK-OPEN-CLOSE

## AIM:
C program using open, read, write, close , create , fork() system calls.
## THEORY:
There are 5 basic system calls that Unix provides for file I/O.

## 1.create:
Used to Create a new empty file

## Syntax :
int create(char *filename, mode_t mode)

## filename :
Name of the file which you want to create

## mode :
Indicates permissions of new file.

## 2. open:
Used to Open the file for reading, writing or both.

## Syntax:
int open(char *path, int flags [ , int mode ] );

## Path :
Path to file which you want to use

## Flags :
How you like to use ?

O_RDONLY: read only, O_WRONLY: write only, O_RDWR: read and write, O_CREAT: create file if it doesn’t exist, O_EXCL: prevent creation if it already exists

## 3. close:
Tells the operating system you are done with a file descriptor and Close the file which pointed by fd.

## Syntax:
int close(int fd); fd :file descriptor

## 4. read:
From the file indicated by the file descriptor fd, the read() function reads cnt bytes of input into the memory area indicated by buf. A successful read() updates the access time for the file.

## Syntax:
int read(int fd, char *buf, int size);

fd: file descripter buf: buffer to read data from cnt: length of buffer

## 5. write:
Writes cnt bytes from buf to the file or socket associated with fd. cnt should not be greater than INT_MAX (defined in the limits.h header file). If cnt is zero, write() simply returns 0 without attempting any other action.

## Syntax:
int write(int fd, char *buf, int size);

fd: file descripter buf: buffer to write data to cnt: length of buffer

*File descriptor is integer that uniquely identifies an open file of the process.

## ALGORITHM:
1. Start the program.

2. Open a file for O_RDWR for R/W,O_CREATE for creating a file ,O_TRUNC for truncate a file.

3. Using getchar(), read the character and stored in the string[] array.

4. The string [] array is write into a file close it.

5. Then the first is opened for read only mode and read the characters and displayed it and close the file.

6. Use Fork().

7. Stop the program.

## PROGRAM:
```
Developed by : MOHAMED AZEEM N
Reg No: 212222110026

#include<sys/stat.h> 
#include<stdio.h> 
#include<fcntl.h> 
#include<sys/types.h> 
int main() 
{ 
int n,i=0; 
int f1,f2; 
char c,strin[100]; 
f1=open("data",O_RDWR|O_CREAT|O_TRUNC); 
while((c=getchar())!='\n') 
{ 
strin[i++]=c; 
 
} 
strin[i]='\0'; 
write(f1,strin,i); 
close(f1); 
f2=open("data",O_RDONLY); 
read(f2,strin,0); 
printf("\n%s\n",strin); 
close(f2); 
fork(); 
return 0; 
 
}
```

## OUTPUT:

![Screenshot (127)](https://github.com/mohamedazeem33/EX.7-IMPLEMENTATION-OF-SYSTEM-CALLS-READ-WRITE-FORK-OPEN-CLOSE/assets/121040764/c44f7302-f88b-44f1-8ae9-c2cc4ebe8c09)

## RESULT:
Thus, open, read, write, close , create , fork() system calls implemented successfully using c program.
