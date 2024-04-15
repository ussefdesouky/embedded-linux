# Embedded Linux

## 1. Linux Fundamentals

### 1.1. Linux System Architecture

![alt_text](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/linux-architecture/linux-architecture.png)

## 2. System Call Interface

![alt_text](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/syscall-interface/Embedded%20Linux-Kernel%20Components.drawio.png)

### 2.1. LAB

#### 2.1.1. Trace $ *ps* command

```
$ strace -c ps
```

- Files of interactions **NONE**.
- Time taken by each syscall and syscall list can be found [here](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/syscall-interface/ps_trace.txt) by executing the command below.

```
$ strace -o ps_trace.txt -c ps
```

- Files of interaction **ps_trace.txt**.

#### 2.1.2. Trace $ *ls* command

```
$ strace -c ls
```

- Files of interactions **NONE**.
- Time taken by each syscall and syscall list can be found [here](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/syscall-interface/ls_trace.txt) by executing the command below.

```
$ strace -o ls_trace.txt -c ls
```

- Files of interaction **ls_trace.txt**.

#### 2.1.3. Trace $ *cd* command

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

## 3. Process Management

### 3.1. LAB

#### 3.1.1. Check how many cores.

```
$ top
```

![top](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/process-management/top.png)

- press 1 to list all the cores you have

  ![cpu-cores](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/process-management/cpu-cores.png)

#### 3.1.2. Create number of cores + 2 processes `dd if=/dev/zero of=/dev/null` run in background.

```
$ for i in {1..22}; do dd if=/dev/zero of=/dev/null & done
```

#### 3.1.3. Change priority for them

```
$ sudo renice -n 20 $(jobs -p)
```

#### 3.1.4. Monitor them using top command

![cpu-cores-increase](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/process-management/cpu-cores-increase.png)

#### 3.1.5. Kill them all using killall command.

```
$ killall dd
```

**OR**

```
$ kill $(jobs -p)
```

- **Note:** this will kill all the background processes.
