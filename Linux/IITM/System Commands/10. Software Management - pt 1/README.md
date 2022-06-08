# Software Management - pt. 1

Date: January 16, 2022
Lecture #: 1
Lecture URL: https://youtu.be/hG-bxCmfArc
Notion URL: https://21f1003586.notion.site/Shell-variables-3c228fce1aef41719f77bc4b8e786ff1
Type: 📒 Lecture
Week #: 4

### Need for a package manager

- Tools for installing, updating, removing, managing software
- Install new/updated software across network
- Package — File look up, both ways
- Database of packages on the system including versions
- Dependency checking
- Signature verification tools
- Tools for building packages

### Package Types

![Untitled](Software%20Management%20-%20pt%201%20b16ede20450b43d79208decb32e1920e/Untitled.png)

![VirtualBox_Manjaro_16_01_2022_22_08_23.png](Software%20Management%20-%20pt%201%20b16ede20450b43d79208decb32e1920e/VirtualBox_Manjaro_16_01_2022_22_08_23.png)

### Architecture

![Untitled](Software%20Management%20-%20pt%201%20b16ede20450b43d79208decb32e1920e/Untitled%201.png)

### To know your system architecture

*~~Can’t spell architecture without arch btw~~*

![VirtualBox_Manjaro_16_01_2022_22_10_51.png](Software%20Management%20-%20pt%201%20b16ede20450b43d79208decb32e1920e/VirtualBox_Manjaro_16_01_2022_22_10_51.png)

### Tools

![Untitled](Software%20Management%20-%20pt%201%20b16ede20450b43d79208decb32e1920e/Untitled%202.png)

### Package Management in Ubuntu using `apt`

**Inquiring package db**

- Search packages for a keyword
    - `apt-cache search keyword`
- List all packages
    - `apt-cache pkgnames`
    - Try `apt-cache pkgnames <starting-char>` to search to packages with the few starting chars
- Display package records of a package
    - `apt-cache show -a package`

### Package names

![Untitled](Software%20Management%20-%20pt%201%20b16ede20450b43d79208decb32e1920e/Untitled%203.png)

### Package priorities

- **required** → essential to the proper functioning of a system
- **important** → provides functionality that enables the system to run well
- **standard** → included in a standard system installation
- **optional** → can omit if you do not have enough storage
- **extra** → could conflict with packages with higher priority, has specialized requirements, install only if needed

### Package sections

[https://packages.ubuntu.com/focal](https://packages.ubuntu.com/focal)

![Untitled](Software%20Management%20-%20pt%201%20b16ede20450b43d79208decb32e1920e/Untitled%204.png)

### Checksums

A way to verify that the packages that we are installing are legit

![Untitled](Software%20Management%20-%20pt%201%20b16ede20450b43d79208decb32e1920e/Untitled%205.png)

`md5sum <filename>` to get the MD5 checksum of a file, use it to compare it to other files

`sha1sum <filename>` to get the SHA1 checksum of a file, use it to compare it to other files

`sha256sum <filename>` to get the SHA256 checksum of a file, use it to compare it to other files