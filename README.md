# OS-EX.6-IMPLEMENTATION-OF-INTER-PROCESS-COMMUNICATION-USING-PIPE

## AIM:
To Write C program to illustrate IPC using pipes mechanisms.

## ALGORITHM:
### Step 1:
Import the os module for process management and communication.
### Step 2:
Define a main() function as the program's entry point.
### Step 3:
Prompt the user to input a message and encode it as bytes.
### Step 4:
Create two pipes, parent_pipe and child_pipe, for communication.
### Step 5:
Fork a child process using os.fork().
### Step 6:
In the child process, close the parent's pipe end and write the message to the child's pipe end.4
### Step 7:
In the child process, close the child's pipe end.
### Step 8:
Exit the child process.
### Step 9:
In the parent process, close the child's pipe end.
### Step 10:
Read the message from the parent's pipe end, decode it, and print it.

## PROGRAM:
```
#include <stdio.h>
int main()
{

  int fd[2],child; char a[10];
  printf("\nEnter the string : ");
  scanf("%s",a);
  pipe(fd);
  child=fork();
  if(!child)
{
    close(fd[0]);
    write(fd[1],a,5); wait(0);
}

  else

{
   close(fd[1]);
    read(fd[0],a,5); printf("The string received from pipe is : %s",a);
}

return 0;
}
```



## OUTPUT:
![i-1](https://github.com/swemurali/OS-EX.6-IMPLEMENTATION-OF-INTER-PROCESS-COMMUNICATION-USING-PIPE/assets/94165336/c1aa48c7-2415-451d-9747-ca99e91d0950)

## Result:
This output confirms that the parent process successfully received and printed the message sent by the child process through the pipe, demonstrating inter-process communication using pipes.


