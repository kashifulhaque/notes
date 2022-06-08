# Bash scripts - pt. 2C

Date: February 9, 2022
Lecture #: 3
Lecture URL: https://youtu.be/kjMhi4gI0po
Notion URL: https://21f1003586.notion.site/Bash-scripts-pt-2C-22f3a0910ba04a088ce5281aab4462e4
Type: 📒 Lecture
Week #: 6

### `eval`

`eval my-arg`

- Executes argument as a shell command
- Combines arguments into a single string
- Returns control to the shell with exit status

```bash
#!/bin/bash
cmd="date";
fmt="+%d-%B-%Y";
eval $cmd $fmt;
```

### Functions in bash

```bash
#!/bin/bash

usage() {
	echo "usage $1 str1 str2";
}

swap() {
	echo "$2 $1";
}

if [ $# -lt 2 ]; then
	usage $0;
	exit 1;
fi;

swap $1 $2;
```

### `getopts`

![Untitled](Bash%20scripts%20-%20pt%202C%20dd0c391fe0d147e4891ab9a81ceaf032/Untitled.png)

```bash
#!/bin/bash
while getopts "ab:c:" options; do
	case "${options}" in
		b)
			barg=${OPTARG};
			echo "accepted: -b $barg";
			;;
		c)
			carg=${OPTARG};
			echo "accepted: -c $carg";
			;;
		a)
			echo "accepted: -b";
			;;
		*)
			echo "Usage: -a -b barg -c carg";
			;;
	esac;
done;
```

Usage

![Untitled](Bash%20scripts%20-%20pt%202C%20dd0c391fe0d147e4891ab9a81ceaf032/Untitled%201.png)

### `select` loop

![Untitled](Bash%20scripts%20-%20pt%202C%20dd0c391fe0d147e4891ab9a81ceaf032/Untitled%202.png)

```bash
#!/bin/bash

echo "select a middle one";
select i in {1..10}; do
    case $i in
        1 | 2 | 3)
            echo "you picked a small one";
            ;;
        8 | 9 | 10)
            echo "you picked a big one";
            ;;
        4 | 5 | 6 | 7)
            echo "you picked the right one";
            break;
            ;;
    esac;
done;

echo "selection completed with $i";
```