# overthewire-bandit
documentation of overthewirebandit progress

---


### level 0

`ssh -p 2220 bandit0@bandit.labs.overthewire.org`

**the syntax is usually**  `ssh user@server `**where i can additionaly use -p to specify port**

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

---

### level 1 -> 2


`cat ./-`  or `cat < -`

`cat -p 2220 bandit2@bandit.labs.overthewire.org '

**when opening a dashed filename i have to specify the full location or alternatively redirect**

referred to [this](https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal)

---

### level 2 -> 3

`cat 'spaces in this filename' `  or `cat spaces\ in\ this\ filename`

`ssh -p 2220 bandit3@bandit.labs.overthewire.org`

**to open files with spaces i have to wrap the file name in '' to indicate it's one singe file or i can use \ to escape spaces**

---

