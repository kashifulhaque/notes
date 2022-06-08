# Networking commands and SSH

Date: March 14, 2022
Lecture #: 4
Lecture URL: https://youtu.be/SxDIXtxR33c
Notion URL: https://21f1003586.notion.site/Networking-commands-and-SSH-9593fb49c2374246b525faff24f19091
Type: 📒 Lecture
Week #: 8

### Network & SSH

Accessing remote machines on command line

### IPv4 address range

- localhost
    - 127.0.0.0/8
- Private network
    - Class A: 10.0.0.0/8
        - 16,777,216
    - Class B: 172.16.0.0/12
        - 1,048,576
    - Class C: 192.168.0.0/16
        - 65,536
- Public network

![Untitled](Networking%20commands%20and%20SSH%20eed91b5d00ed4ebeab2677eb725fcb81/Untitled.png)

### Ways to gain remote access

- VPN access
- SSH tunnelling
- Remote desktop: x2go, rdp, pcoip
- Desktop over browser: Apache Guacomole
- Commercial, over internet: Teamviewer, AnyDesk, Zoho assist, ...

### Some important ports

![Untitled](Networking%20commands%20and%20SSH%20eed91b5d00ed4ebeab2677eb725fcb81/Untitled%201.png)

### Firewall

- Ports open on my machine
- Ports needed to be accessed on remote machine
- Network routing over the port
- Firewall controls at each hop

### Protecting a server

![Untitled](Networking%20commands%20and%20SSH%20eed91b5d00ed4ebeab2677eb725fcb81/Untitled%202.png)

### SELinux

- Security Enhanced Linux mode available on Ubuntu too, apart from server grade flavours like CentOS, Fedora, RHEL, SuSE Linux, etc.
- Additional layer of access control on files to services
- Role Based Access Control
- Process sandboxing, least privilege access for subjects
- Check using `ls -lZ` and `ps -eZ`
- RBAC items:
    - user (unconfined_u)
    - role (object_r)
    - type (user_home_t)
    - level (s0)
- Modes:
    - disabled
    - enforcing
    - permissive
- Tools:
    - semanage
    - restorecon

SELinux is recommended for all publicly visible servers

### Network tools

![Untitled](Networking%20commands%20and%20SSH%20eed91b5d00ed4ebeab2677eb725fcb81/Untitled%203.png)

### High Performance Computing

- Look at [www.top500.org](http://www.top500.org) for statistics
- Accessing a remote HPC machine is usually over SSH
- Long durations jobs are submitted to a job scheduler for execution
- Raw data if large needs to be processed remotely before being transferred to your machine
- Comfort with the command line is a must

![Untitled](Networking%20commands%20and%20SSH%20eed91b5d00ed4ebeab2677eb725fcb81/Untitled%204.png)

Using 3rd party DNS lookup tool

![Untitled](Networking%20commands%20and%20SSH%20eed91b5d00ed4ebeab2677eb725fcb81/Untitled%205.png)

Tool used here: [https://tools.keycdn.com/dig](https://tools.keycdn.com/dig)

![Untitled](Networking%20commands%20and%20SSH%20eed91b5d00ed4ebeab2677eb725fcb81/Untitled%206.png)

![Untitled](Networking%20commands%20and%20SSH%20eed91b5d00ed4ebeab2677eb725fcb81/Untitled%207.png)

To do a reverse lookup

![Untitled](Networking%20commands%20and%20SSH%20eed91b5d00ed4ebeab2677eb725fcb81/Untitled%208.png)