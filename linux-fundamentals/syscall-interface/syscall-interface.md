# System Call Interface

![alt_text](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/syscall-interface/Embedded%20Linux-Kernel%20Components.drawio.png)

## LAB

### Trace $ *ps* command

```
$ strace -c ps
```

- Files of interactions **NONE**.
- Time taken by each syscall and syscall list can be found [here](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/syscall-interface/ps_trace.txt) by executing the command below.

```
$ strace -o ps_trace.txt -c ps
```

- Files of interaction **ps_trace.txt**.

### Trace $ *ls* command

```
$ strace -c ls
```

- Files of interactions **NONE**.
- Time taken by each syscall and syscall list can be found [here](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/syscall-interface/ls_trace.txt) by executing the command below.

```
$ strace -o ls_trace.txt -c ls
```

- Files of interaction **ls_trace.txt**.

### Trace $ *cd* command

```
$ strace -c cd
```

- **Error:** `strace: Can't stat 'cd': No such file or directory`
- **Note:** ***cd*** do not have an executable in the bin directory like ***ls*** and ***ps*** commands, because it's built in the shell.
- **Solution:** Trace a bash that runs the ***cd*** command
- Time taken by each syscall and syscall list can be found [here](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/syscall-interface/cd_trace.txt) by executing the command below.

```
$ strace -o cd_trace.txt -c sh -c "cd"
```

- **Files of interaction:** the directory you want to go, ex: Downloads and **cd_trace.txt**.