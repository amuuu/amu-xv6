# What does this code do?
The following code adds some timers, 3 system calls, and also adds two scheduling mechanisms besides the default round robin algorithm to xv6.

- The first system call is `waitx`. It's similar to the original *wait* system call but it returns the running time and waiting time of the process. Beside these two outputs, 4 timers have been added to the proc structure; start time, end time, I/O time, and remaining time.
- The second system call is `setpriority`. Using this sys call, you can set a priority for the process that's calling it. It's used in the scheduler type 1 algorithm in which it chooses the processes with higher priorities first.
- The thirg system call is `nice` which is used when you want xv6 to use multi-level priority queues to choose between processes. It's used in the type 2 scheduler algorithm. (for further info about the types that I've added, read the `proc.c` file)

## Some tips for playing with xv6:
- If you want to add a new normal* system call, you should edit these files: `proc.c`, `defs.h`, `syscall.c`, `sysproc.c`, `user.h`, `usys.S`, and `syscall.h`. 
- In kernel mode, you can't use malloc to allocate memory. If you want to allocate memory for your struct, arrays, or anything, your only option is using `memset`.
- If you want to return multiple values from a system call, you **can't** return a pointer to an array because the program which is calling the system call, is in the user mode (the array is allocated in kernel mode) and doesn't have access to the place that array exists in memory. **Instead**, you can pass pointers in to the system call function and have the system call fill those pointers and return them to the program which is calling the system call. In this case, the pointers were initialized in the user mode and there won't be any problems.
- This one might sound obvious, but if you want to add a new file, you should also change the Makefile in order for it to be compiled.

## How to run?
On linux, install "qemu." Then on the root directory of this project, run this command:
```
make qemu
```
You can also make the project without running xv6:
```
make
```

## More Information
For more information about xv6 visit: http://pdos.csail.mit.edu/6.828/2016/xv6.html

It might still have some bugs. Feel free to make a pull request and fix it!
