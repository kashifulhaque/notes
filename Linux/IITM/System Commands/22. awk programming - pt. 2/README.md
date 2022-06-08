# awk programming - pt. 2

Date: February 9, 2022
Lecture #: 5
Lecture URL: https://youtu.be/g9_ij64u8eQ
Notion URL: https://21f1003586.notion.site/awk-programming-pt-2-b59debe0a4b54507a20eadf4bc0e1042
Type: 📒 Lecture
Week #: 6

### Arrays

- Associative arrays
- Sparse storage
- Index need not be integer
- `arr[index]=value`
- `for (var in arr)`
- `delete arr[index]`

### Loops

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled.png)

`awk` program to calculate the total fee, avg fee and the roll numbers (and their fee) of those who paid less than a threshold from a garbled data file

`block-ex6.awk`

```bash
#!/usr/bin/gawk -f
BEGIN {
    print "Report of fee paid:";
    totfee=0;
    FS=" ";
}
{
    # print $0;
    if ($1 ~ /[[:alpha:]]{2}[[:digit:]]{2}[[:alpha:]][[:digit:]]{3}+/) {
        roll=$1;
        fee=$2;
        rf[roll]=fee;
        totfee += fee;
        print roll " paid " fee;
    }
}
END {
    cutoff=21500;
    print "List of students who paid less than " cutoff;
    ns=0;
    for (r in rf)
    {
        ns++;
        if(rf[r] < cutoff) print "check ", r, " paid only " rf[r];
    }
    avg = totfee/ns;
    print "Total fee collected:" totfee;
    print "Average fee collected:" avg;
}
```

*Input*

`block-ex6.input`

```
This file contains comments and numbers
Lines containing roll number and the fee paid need to be picked up
mm22b901  21000
Sum of the total fee paid needs to be printed at the end
Also a list of students, who paid how much
mm22b902 21000
Input text may contain some commends in between
mm22b906      21800
mm22b903 21500 paid through DD
mm22b905   22000
updated as on Jan 26, 2022 by Phani
```

Output

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%201.png)

### functions

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%202.png)

`func-lib.awk`

```bash
function myfunc1() {
    printf "%f\n", 2*$1;
}
function myfunc2(a) {
    # Adding zero to 'a' here just to store the value in 'b' as an integer
    b=a+0;
    return sin(b);
}
```

`func-example.awk`

```bash
BEGIN {
    FS=":";
    print "---------- BEGIN ----------";
    c=atan2(1,1);
    print "c=" c;
    print "---------------------------";
}
{
    print $0;
    myfunc1();
    a=$1;
    b=myfunc2(a);
    print "b=" b;
}
END {
    print "---------- ADD ----------";
    d=myfunc2(c);
    print "d=" d;
    print "-------------------------";
}
```

Output

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%203.png)

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%204.png)

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%205.png)

### Pretty printing

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%206.png)

### `bash` + `awk`

- Including awk inside shell script
- heredoc feature
- Use with other shell scripts on command line using pipe

### Examples

The following code creates 3 columns of 10 rows filled with random numbers

We also need to pass an input string for this code

But as we do not have a body for the action block, empty string suffices

`rsheet-create.awk`

```bash
#!/usr/bin/gawk -f
BEGIN {
    nl = 10;
    nc = 3;
    for(j=0; j<nl; j++) {
        for(i=0; i<nc; i++) {
            printf("%f ", rand());
        }
        printf("\n");
    }
}
{}
END {
    print nl " lines with " nc " columns of random numbers created";
}
```

Output

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%207.png)

Now, we can modify the above code to generate 2 columns of 2 million rows filled with random numbers

We will pass the empty file `xaa` we created earlier, and also use the command `time` to calculate the time taken to execute

```bash
#!/usr/bin/gawk -f
BEGIN {
    nl = 2000000;
    nc = 2;
    for(j=0; j<nl; j++) {
        for(i=0; i<nc; i++) {
            printf("%f ", rand());
        }
        printf("\n");
    }
}
{}
END {
    # print nl " lines with " nc " columns of random numbers created";
}
```

Output

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%208.png)

*Welp, it took a long time on my* 🥔 *laptop*

Now, we should process these numbers and create 2 more rows after that which would contain the product and the sum of these numbers

`rsheet-process.awk`

```bash
#!/usr/bin/gawk -f
BEGIN {
    OFS=" ";
    FS=" ";
}
{
    prod = $1*$2;
    sum = $1+$2;
    printf("%f %f %f %f\n", $1, $2, prod, sum);
}
END {}
```

Input is the `rsheet-data.txt` file generated earlier

Output

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%209.png)

---

An awk program to know the IP addresses of all the clients that connected to our web server (Apache) in the last 5 days

Server log file [76.6MB]: [https://firebasestorage.googleapis.com/v0/b/fb-sandbox-25.appspot.com/o/access-full.log?alt=media&token=b1e22c89-5f85-4e12-8087-dfe50fa0e49d](https://firebasestorage.googleapis.com/v0/b/fb-sandbox-25.appspot.com/o/access-full.log?alt=media&token=b1e22c89-5f85-4e12-8087-dfe50fa0e49d)

***To get the IP addresses***

*Type the following code on the bash terminal*

```bash
awk 'BEGIN {FS=" "}{print $1}' access-head.log
```

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2010.png)

```bash
awk 'BEGIN {FS=" "}{print $1}' access-tail.log
```

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2011.png)

Here, `access-head.log` and `access-tail.log` are the top 10 and bottom 10 lines of the file `access-full.log` respectively

***Similarly, to get the date***

*Type the following code on the bash terminal*

```bash
awk 'BEGIN {FS=" "}{d=substr($4,2,11); print d}' access-head.log
```

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2012.png)

```bash
awk 'BEGIN {FS=" "}{d=substr($4,2,11); print d}' access-tail.log
```

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2013.png)

Now, combine the above 2 scripts (one from the IP address one, one from the date one) to get the IP address and the date on which they connected to the server

```bash
awk 'BEGIN {FS=" "}{d=substr($4,2,11); print d, $1}' access-head.log
```

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2014.png)

```bash
awk 'BEGIN {FS=" "}{d=substr($4,2,11); print d, $1}' access-tail.log
```

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2015.png)

Now, run it on the entire log file and `time` it too. Also save it to a file named `date-ip.txt`

```bash
time awk 'BEGIN {FS=" "}{d=substr($4,2,11); print d, $1}' access-full.log > date-ip.txt
```

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2016.png)

---

Statistics time 😐

To calculate the number of connections per day from the log file

***To get the datestring for the last n days***

```bash
date --date="<n> days ago" +%d/%m/%Y
```

**NOTE:** Replace the `<n>` with the actual number

***Example***

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2017.png)

**Code**

`apache-log-ex1.awk`

```bash
#!/usr/bin/gawk -f
BEGIN {
	ndays=15;
	dformat="+%d/%b/%Y";
	for(i=0; i<ndays; i++) {
		cmdstr=sprintf("date --date=\"%d days ago\" %s", i, dformat);
		cmdstr | getline mydate;
		dates[i]=mydate;
	}
	dstring = "";
	for (i in dates) {
		dstring = dstring " " dates[i];
	}
	print "date string=" dstring;
}
{
	ldate=substr($4,2,11);
	w = match(dstring,ldate);
	if(w != 0) {
		# print ldate " " $1 " " $7;
		print ldate " " $1;
		ipcount[$1]++;
	}
}
END {
	print "------------ IP STATS ------------";
	for (j in ipcount) {
		print j " "ipcount[j];
	}
}
```

Input

`access-head.log` or `access-tail.log` or `access-full.log`

Output

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2018.png)

### DNS lookup utility

Command: `dig`

Usage: `dig -x <ip-address>`

***Example***

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2019.png)

To get a slimmer output: `dig +noall +answer -x 34.234.167.93`

***Example***

![Untitled](awk%20programming%20-%20pt%202%202cc1aaeeed324295a604045d3786c2f7/Untitled%2020.png)

Previous `awk` code, modified

```bash
#!/usr/bin/gawk -f
BEGIN {
	ndays=25;
	dformat="+%d/%b/%Y";
	for(i=0; i<ndays; i++) {
		cmdstr=sprintf("date --date=\"%d days ago\" %s", i, dformat);
		cmdstr | getline mydate;
		dates[i]=mydate;
	}
	dstring = "";
	for (i in dates) {
		dstring = dstring " " dates[i];
	}
	print "date string=" dstring;
}
{
	ldate=substr($4,2,11);
	w = match(dstring,ldate);
	if(w != 0) {
		# print ldate " " $1 " " $7;
		# print ldate " " $1;
		ipcount[$1]++;
	}
}
END {
	print "------------ IP STATS ------------";
	for (j in ipcount) {
		print j " "ipcount[j];
        cmdstr = sprintf("dig +noall +answer -x %s", j);
        cmdstr | getline ipinfo;
        print ipinfo;
	}
}
```