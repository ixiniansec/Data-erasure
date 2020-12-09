**This project records the secure erasure of all data in the Linux system.**

OS:Centos
If you use other Linux distributions, please obtain the following programs through the corresponding package manager.



plan 1: Secure-Delete

```
sudo yum install secure-delete
```

then, you can use the `srm` command to delete files.
The `srm` command works similarly to the `rm` command, but it is more than just deleting a file. It first rewrites the file several times with some random data, and then deletes the file completely.

```
sudo srm  /datas/*
```

`sfill` detects the space marked as free or available in the specified partition or directory, and then uses its own algorithm to fill it with some random data. Therefore, it ensures that there are no files or folders that can be recovered on this partition.

```
sudo sfill /home
```

The `sswap` command is used to safely clear your swap partition. The swap partition is used to store data for running programs.

```
sudo sswap /dev/sda5
```

`Smem` is used to clean up the content in the memory. Although the content in the random access memory (RAM) will be cleaned up when the system is restarted or shut down, some residual traces of data will still remain in the memory. This command provides safe memory cleaning, just run the `smem` command in the terminal.






plan2: shred

Use the shred tool to run the following command to delete the file:
```
shred /home/test.jpg
```

plan3: dd (recommend)

```
dd if=/dev/zero of=/dev/sda bs=2MB oflag=nonblock
```

plan3: wipe(slow)

```
sudo yum install wipe
```

Delete Files:
```
wipe filename
```

Delete the contents of the complete partition:
```
wipe /dev/sda1
```



