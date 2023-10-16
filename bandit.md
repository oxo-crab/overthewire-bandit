# overthewire-bandit
documentation of overthewirebandit progress

---


### level 0

`ssh -p 2220 bandit0@bandit.labs.overthewire.org`

**the syntax is usually**  `ssh user@server `**where i can additionaly use -p to specify port**

*password - bandit0*

---

### level 0 -> 1

` cat readme `

`ssh -p 2220 bandit1@bandit.labs.overthewire.org`

**learned about various commands like**

    -cat
    -ls
    -cd
    -file
    -du
    -find

**i can also use ctrl+d to terminate the ssh session**

*password - NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL*

---

### level 1 -> 2


`cat ./-`  or `cat < -`

`cat -p 2220 bandit2@bandit.labs.overthewire.org '

**when opening a dashed filename i have to specify the full location or alternatively redirect**

*referred to [this](https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal)*

*password - rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi*

---

### level 2 -> 3

`cat 'spaces in this filename' `  or `cat spaces\ in\ this\ filename`

`ssh -p 2220 bandit3@bandit.labs.overthewire.org`

**to open files with spaces i have to wrap the file name in '' to indicate it's one singe file or i can use \ to escape spaces**

*referred to [this](https://linuxhandbook.com/filename-spaces-linux/)*

*password - aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG*

---

### level 3 -> 4

1.  `ls`
2.  `cd inhere`
3.  `find`
4.  `cat .hidden`

 `ssh -p 2220 bandit4@bandit.labs.overthewire.org`

**used** `ls` **to list out content of directories, found 'inhere' directory, used** `cd` **to change directory, used** `find` **to find files in 'inhere', can alternatively use** `ls -a`, `-a` **is used to show files that start with a ' . '**

*referred to [this](https://man7.org/linux/man-pages/man1/ls.1.html) regarding *`ls -a`

*password -2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe*

---

### level 4 -> 5

1.  `ls -a`
2.  `cd inhere`
3.  `ls -a -h`
4.  `cat < -file07`

`ssh -p 2220 bandit5@bandit.labs.overthewire.org`

**used** `-h` **to include human readable file**

*referred to [this](https://man7.org/linux/man-pages/man1/ls.1.html)*

*password - lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR*

---
### level 5 ->6


1.  `cd inhere`
2.  `find -size 1033c`
3.  `cat ./maybehere07/.file2`
4.  `ssh -p 2220 bandit6@bandit.labs.overthewire.org`

**filter out files by using the size given which is 1033 bytes, bytes is represented by c**

*referred to [this](https://man7.org/linux/man-pages/man1/find.1.html)*

*password - P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU*

--

### level 6 -> 7

1.  `cd ..`
2.  `find ../ -type f -size 33c -user bandit7 -group bandit6`
3.  `cat ../var/lib/dpkg/info/bandit7.password`
4.  `ssh -p 2220 bandit7@bandit.labs.overthewire.org`


**i decided to go back one directory since it says file is in the server, then use find**`../ `**to find further back, **`-type`** filers by making output to be only file and output is being further filtered by** `-user` **and** `-group`

**this throws out lot of results with permission denied in several files, finding the password location within is hard. This can be fixed by introducing** `2>/dev/null`  **at the end of find command,it writesall the error output in 'void'** 

*referred to this [this](https://unix.stackexchange.com/questions/70963/difference-between-2-2-dev-null-dev-null-and-dev-null-21) and [this](https://man7.org/linux/man-pages/man1/find.1.html)*

*password - z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S*

---

### level 7 -> 8

1.  `strings data.txt| grep millionth`
2.  `ssh -p 2220 bandit8@bandit.labs.overthewire.org`


**using a new command** `strings` **and** `grep`, **strings output all the strings from the file and grep prints line that matches pattern**

**the key is, password is next to word 'millionth', so by adding pipe '|', i can filter the strings with grep**

*password - TESKZC0XvTetK0S9xNwm25STk5iWrBvP*

---


