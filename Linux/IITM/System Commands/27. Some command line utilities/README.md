# Some command line utilities

Date: March 14, 2022
Lecture #: 3
Lecture URL: https://youtu.be/fNf74ycgD9w
Notion URL: https://21f1003586.notion.site/Some-command-line-utilities-acc242cefc3e4312a522a61e2befebe6
Type: 📒 Lecture
Week #: 8

### Utilities

- `find` → locating files and processing them
- `tar, gzip` etc. → packaging collections of files
- `make` → conditional actions

### `find`

Usage: `find [pathnames] [conditions]`

![Untitled](Some%20command%20line%20utilities%208f50be9af35247bba21de13bf8735ee7/Untitled.png)

### file packaging

- Deep file hierarchies
- Large number of tiny files
- `tar` → collect a file hierarchy into a single file
- `gzip` → compress a file
- **Applications** → backup, file sharing, reduce disc utilization

### Possibilities

- `tar, zip`
- `compress` (ncompress), `gzip` (ncompress), `bzip2` (bzip2), `xz` (xz-utils), `7z` (p7zip-full)
- Tarballs like `bundle.tgz` for package + compress
- Time & memory required to shrink / expand versus size ratio
- Portability
- Unique names using timestamp, process ID etc., for backup tarballs

### `make`

Usage: `make -f make.file`

![Untitled](Some%20command%20line%20utilities%208f50be9af35247bba21de13bf8735ee7/Untitled%201.png)

### To compress using `tar`

`tar -cvf filename.tar foldername/`

### To compress `.tar` file using `gzip`

`gzip filename.tar`

### To uncompress a `.gz` file

`gunzip filename.tar.gz`

### To compress a `.tar` file using `bzip2`

`bzip2 filename.tar`

### To uncompress a `.bz2` file

`bzip2 -d filename.tar.bz2`

### To compress a `.tar` file using `compress`

`compress filename.tar`

### To uncompress a `.Z` file

`uncompress filename.tar.Z`

### To un-tar a file

`tar -xzvf filename.tar`

-xzvf → How to remember?

**eXtract Ze Vucking Files**