## 3. Process Management

### LAB 3

1. Check how many cores.

```
$ top
```

![top](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/process-management/top.png)

- press 1 to list all the cores you have

![cpu-cores](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/process-management/cpu-cores.png)

2. Create number of cores + 2 processes `dd if=/dev/zero of=/dev/null` run in background.

```
$ for i in {1..22}; do dd if=/dev/zero of=/dev/null & done
```

3. Change priority for them

```
$ sudo renice -n 20 $(jobs -p)
```

4. Monitor them using top command

![cpu-cores-increase](https://github.com/ussefdesouky/embedded-linux/blob/master/linux-fundamentals/process-management/cpu-cores-increase.png)

5. Kill them all using killall command.

```
$ killall dd
```

**OR**

```
$ kill $(jobs -p)
```

- **Note:** this will kill all the background processes.
