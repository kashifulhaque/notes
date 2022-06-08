# Version Control

Date: February 21, 2022
Lecture #: 2
Lecture URL: https://youtu.be/tzYx6DKtvGw
Notion URL: https://21f1003586.notion.site/Version-Control-bff372d37e544b94a72544dafd13d3c7
Type: 📒 Lecture
Week #: 7

### Version Control

A group of programmers are working on a major project → tons of code in various files (modular approach)

Each programmer has multiple versions of each file they worked on

So, the basic idea of version control → trace back to a working version of code

**Some version control systems are ...**

**SVN →** Centrally hosted & managed version system

It has one master that keeps track of what version of the code that we are officially supporting

Then the master is going to ensure that the same version is replicated by others

**Git →** Distributed version control system

### RAID

Redundant Array of Inexpensive/Independent Disks

It is a data storaga virtualization technology that combines multiple physical disk drive components into one or more logical units for the purposes of data redundancy, performance improvement or both

Since it is an array, it not only provides redundacy, but also speeds up the data access speed

As the speed limit of SATA interface is 6Gb/s, and we have 3 disks in an RAID array

When we access a file that is stored in 3 parts in those 3 disks, we can effectively utilize upto 18Gb/s of bandwidth

Workstations usually come with a RAID controller (it is a PCI card) and it determines how fast we can access data and the capacity of disks too

**Hot Spare →** It is a disk that we keep plugged in but it is not in use, but if any of the disks were to fail, the hot spare is automatically put to use

In a RAID config, **usable space < actual space**

Suppose, we have 4 x 8TB disks, so the actual space if 32TB, but the usable space might be 26TB

### Git

- Distributed
- If the “master” server is hacked
    - Not much of an issue as every user (collaborator) has a copy of everything
- It doesn’t require a server, but we can have a server
- **remote →** It is a server with which we sync our code, usually considered as the master version
- **Protocol used →** `git`
- Options to run git →
    - locally run git server
    - campus git server
    - gitlab
    - github

*Git Cheat Sheet: [https://education.github.com/git-cheat-sheet-education.pdf](https://education.github.com/git-cheat-sheet-education.pdf)*