# Knowing your Hardware

Date: March 14, 2022
Lecture #: 1
Lecture URL: https://youtu.be/pbb5YQQhqXU
Notion URL: https://21f1003586.notion.site/Knowing-your-Hardware-5b54e4c1a93d457cbbe4be4a76f3d7fc
Type: 📒 Lecture
Week #: 8

### Packages to know hardware

```bash
clinfo, coreutils, dmidecode, fdisk, hardinfo, hdparm, hwinfo, lshw
memtester, net-tools, pciutils, procps, sysstat, upower, util-linux
```

### `hwinfo`

Gives us the hardware info

### `lshw`

Lists the hardware

***Example***

![Untitled](Knowing%20your%20Hardware%2046587c2e32d14fda9dbfa5ba2b5f5d85/Untitled.png)

### To get details about the CPU

`cat /proc/cpuinfo`

### Get details about the partitions

`cat /proc/partitions`

![Untitled](Knowing%20your%20Hardware%2046587c2e32d14fda9dbfa5ba2b5f5d85/Untitled%201.png)

### How many block type devices (storage devices)?

`lsblk`

![Untitled](Knowing%20your%20Hardware%2046587c2e32d14fda9dbfa5ba2b5f5d85/Untitled%202.png)

Gives us just the NAME and the SIZE

![Untitled](Knowing%20your%20Hardware%2046587c2e32d14fda9dbfa5ba2b5f5d85/Untitled%203.png)

### List all the PCIe devices

`lspci`

![Untitled](Knowing%20your%20Hardware%2046587c2e32d14fda9dbfa5ba2b5f5d85/Untitled%204.png)

### To know the # of DIMM modules installed

`sudo dmidecode --type memory`

Requires super user

### Look at system details in the GUI

`hardinfo`

Make sure to install it first, 

Might not work in WSL (Use WSLg for the GUI)

### To know details about the GPU

`clinfo`

### To know the battery status

`upower -e`

It will list a bunch of names, copy the entire path of your battery

`upower -i <battery-path>`

### Storage benchmark?

`sudo hdparm -Tt /dev/sda`

Requires super user

![Untitled](Knowing%20your%20Hardware%2046587c2e32d14fda9dbfa5ba2b5f5d85/Untitled%205.png)

### To know CPU and Storage usage (realtime?)

`iostat -dx /dev/sda`

![Untitled](Knowing%20your%20Hardware%2046587c2e32d14fda9dbfa5ba2b5f5d85/Untitled%206.png)

*The numbers, Mason, what do they mean?*

### To know the network config

`ifconfig`

![Untitled](Knowing%20your%20Hardware%2046587c2e32d14fda9dbfa5ba2b5f5d85/Untitled%207.png)