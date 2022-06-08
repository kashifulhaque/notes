# awk programming - pt. 1

Date: February 9, 2022
Lecture #: 4
Lecture URL: https://youtu.be/k3q-9ntZI4s
Notion URL: https://21f1003586.notion.site/awk-programming-pt-1-63f859576b6c4836a7cc2ed96ac4c99b
Type: 📒 Lecture
Week #: 6

### `awk`

A language for processing fields and records

### Introduction

- It is a programming language
- `awk` is an abbreviation of the 3 people who developed it
    - **A**ho
    - **W**einberger
    - **K**ernighan
- It is a part of POSIX, IEEE 1003.1-2008
- Variants of `awk`
    - `nawk`
    - `gawk`
    - `mawk`
    - `...`
- `gawk` contains features that extend POSIX

### Execution model

- Input stream is a set of records
    - Eg. using `“\n”` as a record separator, lines are recorded
- Each record is a sequence of fields
    - Eg. using `“ ”` as a field separator, words are fields
- Splitting of records to fields is done automatically
- Each codeblock executes on one record at a time, as matched by the pattern of that block

### usage

- Single line at the command line
    
    `cat /etc/passwd | awk -F”:” ‘{print $1}’`
    
- Script interpreted by awk
    
    `./myscript.awk /etc/passwd`
    
    `myscript.awk` 👇
    
    ```bash
    #!/usr/bin/gawk -f
    BEGIN {
    	FS=":"
    }
    {
    	print $1
    }
    ```
    

**Example #1**

Block example

It does one print statement to illustrate how many times each codeblock is being processed

```bash
#!/usr/bin/gawk -f
BEGIN {
    print "BEGIN action is processed";
}
{
    print "Default action is processed";
}
END {
    print "END action is processed";
}
```

```
line-1 word1a word1b word1b
line-2 word2a word2b word2b
line-3 word3a word3b word3c
```

Output

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled.png)

### Built-in variables

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%201.png)

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%202.png)

### `awk` scripts

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%203.png)

### execution

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%204.png)

### operators

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%205.png)

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%206.png)

### Functions and Commands

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%207.png)

```bash
#!/usr/bin/gawk -f
BEGIN {
    print "BEGIN action is processed";
}
{
    print "record: " $0;
    print "processing record number: " FNR;
    print "number of fields in the current record: " NF;
}
END {
    print "END action is processed";
}
```

```
line-1 word1a word1b word1b
line-2 word2a word2b
line-3 word3a
```

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%208.png)

```bash
#!/usr/bin/gawk -f
BEGIN {
    print "BEGIN action is processed";
}
/[[:alpha:]]/ {
    print "alpha record: " FNR ":" $0;
    print "number of fields in the current record: " NF;
}
/[[:alnum:]]/ {
    print "alnum record: " FNR ":" $0;
    print "number of fields in the current record: " NF;
}
/[[:digit:]]/ {
    print "digit record: " FNR ":" $0;
    print "number of fields in the current record: " NF;
}
END {
    print "END action is processed";
}
```

```
hello world welcome to awk
mm22b901 name place
600036 mm23b902 name
04422574770 231
```

Output

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%209.png)

To match only the first field, instead of the entire record

```bash
#!/usr/bin/gawk -f
BEGIN {
    print "BEGIN action is processed";
}
$1 ~ /[[:alpha:]]/ {
    print "alpha record: " FNR ":" $0;
    print "number of fields in the current record: " NF;
}
$1 ~ /[[:alnum:]]/ {
    print "alnum record: " FNR ":" $0;
    print "number of fields in the current record: " NF;
}
$1 ~ /[[:digit:]]/ {
    print "digit record: " FNR ":" $0;
    print "number of fields in the current record: " NF;
}
END {
    print "END action is processed";
}
```

*Input is the same as the previous*

Output

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%2010.png)

---

In the following example, we don't do any pattern matching or comparison

Instead, we look at the number of fields in any particular (or arbitrary) record

```bash
#!/usr/bin/gawk -f
BEGIN {
    print "BEGIN action is processed";
    FS="[ .;:-]";
}
NF > 2 {
    print "acceptable record:" FNR ":" $0;
    print "number of fields in the current record:" NF;
}
NF <= 2 {
    print "not acceptable record:" FNR ":" $0;
    print "number of fields in the current record:" NF;
}
END {
    print "END action is processed";
}
```

*Input*

```
hello:world:welcome to awk
mm22b901;name;place
600036-mm23b902-name
04422574770 231 12345
gphani@iitm.ac.in
```

Output

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%2011.png)

We can modify the FS (field separator) in the above script to not allow `" "` (space) and `"."` (dot) as the field separator

The result will change

*Modified code* (Notice line #4)

```bash
BEGIN {
    print "BEGIN action is processed";
    FS="[;:-]";
}
NF > 2 {
    print "acceptable record:" FNR ":" $0;
    print "number of fields in the current record:" NF;
}
NF <= 2 {
    print "not acceptable record:" FNR ":" $0;
    print "number of fields in the current record:" NF;
}
END {
    print "END action is processed";
}
```

*Input is the same as previous unmodified one*

Output

![Untitled](awk%20programming%20-%20pt%201%202b7d93c820f64da5817679ef374d28d6/Untitled%2012.png)