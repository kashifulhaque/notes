# Bash scripts - pt. 2B

Date: February 9, 2022
Lecture #: 2
Lecture URL: https://youtu.be/n56JIC15DBo
Notion URL: https://21f1003586.notion.site/Bash-scripts-pt-2B-caebca1e09d24acfba760344452db02d
Type: 📒 Lecture
Week #: 6

### `if-elif-else-fi` loop

![Untitled](Bash%20scripts%20-%20pt%202B%20305c3b81cbe04755b5bc72d6a9e7664d/Untitled.png)

```bash
#!/bin/bash

if [ $# -gt 2 ]; then
    echo "More than 2 arguments";
elif [ $# -gt 1 ]; then
    echo "More than 1 argument";
elif [ $# -gt 0 ]; then
    echo "Not enough arguments";
else
    echo "Arguments required";
fi;
```

### `case` statement options

![Untitled](Bash%20scripts%20-%20pt%202B%20305c3b81cbe04755b5bc72d6a9e7664d/Untitled%201.png)

```bash
#!/bin/bash

echo "What is your favourite image processor?";
read pname;

case $pname in
    [gG]imp | inkscape)
        echo "Good choice";
        ;;
    [aA]dobe*)
        echo "Absolutely proprietary and costs a lot";
        ;;
    imagej)
        echo "Measuring things on the image?";
        ;;
    *)
        echo "$pname is a new find for me";
        ;;
esac;
```

*When you enter “adobe”*

![https://ih0.redbubble.net/image.766090717.2879/flat,1000x1000,075,f.jpg](https://ih0.redbubble.net/image.766090717.2879/flat,1000x1000,075,f.jpg)

### C-style `for` loop → one variable

![Untitled](Bash%20scripts%20-%20pt%202B%20305c3b81cbe04755b5bc72d6a9e7664d/Untitled%202.png)

```bash
#!/bin/bash

begin=1;
finish=10;

for (( a = $begin; a < $finish; a++ )); do
    b=$(( a**2 ));
    echo $b;
done;
```

### C-style `for` loop → two variables

![Untitled](Bash%20scripts%20-%20pt%202B%20305c3b81cbe04755b5bc72d6a9e7664d/Untitled%203.png)

*NOTE: only one condition to close out the for loop*

```bash
#!/bin/bash

begin1=1;
begin2=20;
finish=10;

for (( a = $begin1, b = $begin2; a < $finish; a++, b-- )); do
    c=$(( a**2 ));
    d=$(( b**2 ));
    echo $c $d;
done;
```

### Processing output of a loop

![Untitled](Bash%20scripts%20-%20pt%202B%20305c3b81cbe04755b5bc72d6a9e7664d/Untitled%204.png)

*NOTE: Output of the loop is re-directed to the tmp file*

```bash
#!/bin/bash

filename=largefile.txt;
if [ -e $filename ]; then
    echo "file $filename exists";
    exit 1;
fi;

i=1;
while [ $i -lt 10 ]; do
    echo "$i $[$i+1]";
    (( i++ ));
done > $filename;

echo "file $filename written";
ls -l $filename;
```

### `break`

To break out of a loop

![Untitled](Bash%20scripts%20-%20pt%202B%20305c3b81cbe04755b5bc72d6a9e7664d/Untitled%205.png)

![Untitled](Bash%20scripts%20-%20pt%202B%20305c3b81cbe04755b5bc72d6a9e7664d/Untitled%206.png)

`break 2` refers to the outer loop as seen from the nesting

### `continue`

Opposite of `break`

![Untitled](Bash%20scripts%20-%20pt%202B%20305c3b81cbe04755b5bc72d6a9e7664d/Untitled%207.png)

### `shift`

![Untitled](Bash%20scripts%20-%20pt%202B%20305c3b81cbe04755b5bc72d6a9e7664d/Untitled%208.png)

It keeps on shifting (read: delete/destroy) the arguments to the left

```bash
#!/bin/bash

echo "Number of args: ";
echo $#;
i=1;

while [ -n "$1" ]; do
    echo "arg $i is $1";
    shift;
    (( i++ ));
done;

echo "Number of args now: ";
echo $#;
```

### `exec`

`exec ./my-executable --my-options --my-args`

- To replace shell with a new program or to change i/o settings
- If new program is launched successfully, it will not return control back to the shell
- If new program fails to launch, the shell continues

```bash
#!/bin/bash
echo "PID of shell running this command: $$";
echo  "Leaving bash and opening xterm if available";
exec xterm;
echo "Looks like xterm is not available or failed to start";
```