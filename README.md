# Linux-Process-API-fork-wait-exec-

# Ex02-OS-Linux-Process API - fork(), wait(), exec()

Operating systems Lab exercise


## AIM :

To write C Program that uses Linux Process API - fork(), wait(), exec()

## DESIGN STEPS :

### Step 1 :

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2 :

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3 :

Test the C Program for the desired output. 

## PROGRAM :

### DEVELOPED BY : DILLIARASU M
### REG NO : 212223230049

## C Program to print process ID and parent Process ID using Linux API system calls :
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```

## OUTPUT :

![image](https://github.com/JoyceBeulah/Linux-Process-API-fork-wait-exec/assets/118343698/c185b57b-3f9d-46bb-8c35-d1d38d480959)


## C Program to create new process using Linux API system calls fork() and exit() :

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
int main() {
    int pid;
    pid = fork();
    if (pid == -1) {
        perror("fork");
        exit(EXIT_FAILURE);
    }
    else if (pid == 0) {
        printf("I am child, my pid is %d\n", getpid());
        printf("My parent pid is: %d\n", getppid());
        exit(EXIT_SUCCESS);
    }
    else {
        printf("I am parent, my pid is %d\n", getpid());
        sleep(100);
        exit(EXIT_SUCCESS);
    }
    return 0;
}
```

## OUTPUT :

![image](https://github.com/JoyceBeulah/Linux-Process-API-fork-wait-exec/assets/118343698/f3fde68b-c98d-4172-a7db-0773758b3ad4)


## C Program to execute Linux system commands using Linux API system calls exec() family :
```
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
int main() {
    pid_t pid = fork();
    if (pid < 0) {
        perror("Fork failed");
        exit(EXIT_FAILURE);
    } else if (pid == 0) {
        printf("This is the child process. Executing 'ls' command.\n");
        execl("/bin/ls", "ls", "-l", NULL); // Lists files in long format
        perror("execl failed");
        exit(EXIT_FAILURE);
    } else {
        int status;
        waitpid(pid, &status, 0); // Wait for the child to finish
        if (WIFEXITED(status)) {
            printf("Child process exited with status %d.\n", WEXITSTATUS(status));
        } else {
            printf("Child process did not exit normally.\n");
        }
        printf("Parent process is done.\n");
    }
    return 0;
}
```


## OUTPUT :

![image](https://github.com/JoyceBeulah/Linux-Process-API-fork-wait-exec/assets/118343698/42dda2d9-9f8a-47d2-b9c5-13dd09b97dd3)


# RESULT :

Thus the programs are executed successfully.












# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
~~~
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
~~~










##OUTPUT



![324707831-cf8214d6-4c03-47ad-a3d3-db6b1df17640](https://github.com/user-attachments/assets/d3e67ed0-8ec2-4d97-9fb1-16527ecf44a8)











## C Program to create new process using Linux API system calls fork() and exit()

~~~
#include <stdio.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}
~~~













##OUTPUT



![324708223-da579391-0b3b-4e89-892f-b842417a4d49](https://github.com/user-attachments/assets/64b42b3c-0dda-486e-89fd-985f30c131a0)





## C Program to execute Linux system commands using Linux API system calls exec() family



~~~
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
int main()
{
	printf("Running ps with execlp\n");
	execlp("ps", "ps", "ax", NULL);
	printf("Done.\n");
	exit(0);
}
~~~






















##OUTPUT



![324708714-a16f872f-5abe-4c3f-90db-e44360ab23d2](https://github.com/user-attachments/assets/ec1a0f60-7b59-499a-8586-218df70c1bea)


#















# RESULT:
The programs are executed successfully.
# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
















##OUTPUT














## C Program to create new process using Linux API system calls fork() and exit()













##OUTPUT








## C Program to execute Linux system commands using Linux API system calls exec() family


























##OUTPUT


















# RESULT:
The programs are executed successfully.
