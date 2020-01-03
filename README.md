# What does this project do?
The following code adds some timers, 3 system calls, and also adds two scheduling mechanisms besides the default round robin algorithm to xv6.

- The first system call is **waitx**. It's similar to the original *wait* system call but it returns the running time and waiting time of the process. Beside these two outputs, 4 timers have been added to the proc structure; start time, end time, I/O time, and remaining time.
- The second system call is **setpriority**. Using this sys call, you can set a priority for the process that's calling it. It's used in the scheduler type 1 algorithm in which it chooses the processes with higher priorities first.
- The thirg system call is **nice** which is used when you want xv6 to use multi-level priority queues to choose between processes. It's used in the type 2 scheduler algorithm. (for further info about the types that I've added, read the *proc.c* file)

## How to run?
On linux, install "qemu." Then on the root directory of this project, run this command:
```
make qemu
```
You can also make the project without running xv6:
```
make
```

For more information about xv6 visit: http://pdos.csail.mit.edu/6.828/2016/xv6.html

It might still have some bugs. Feel free to make a pull request and fix it!
