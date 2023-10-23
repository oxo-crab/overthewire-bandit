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
3.  `file ./*`
4.  `cat < -file07`

`file ./*` **with this the type fo file in inhere can be determinded, there is only one file with ascii characters**

`ssh -p 2220 bandit5@bandit.labs.overthewire.org`


*referred to [this](https://man7.org/linux/man-pages/man1/ls.1.html)* *and [this](https://mayadevbe.me/posts/overthewire/bandit/level5/) for the use of*`file ./*`

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

*referrencing [this](https://man7.org/linux/man-pages/man1/grep.1.html) and [this](https://www.man7.org/linux/man-pages/man1/strings.1.html)*

*password - TESKZC0XvTetK0S9xNwm25STk5iWrBvP*

---

### level 8 -> 9

1.  `cat data.txt|sort|uniq -u`
2.  `ssh -p 2220 bandit9@bandit.labs.overthewire.org`

**it's necessary to use sort before applying uniq command as unique only removes [succesive duplicate lines](https://www.man7.org/linux/man-pages/man1/uniq.1.html)** 

*password - EN632PlfYiZbn3PhVK3XOGSlNInNE00t*

---

### level 9->10 

1.  `strings data.txt| grep ===`
2.  `ssh -p 2220 bandit10@bandit.labs.overthewire.org`

**as strings is capable of printing sequences of printablle characters, it's a better fit compared to cat as the file is binary, and the data is messy and overlapping over the password,this way only 'human-readable' text shows up**

*password - G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s*

---
### level 10 -> 11


1.  `base64 -d data.txt`
2.  `ssh -p 2220 bandit11@bandit.labs.overthewire.org`

**question directly states that data is base64 encoded.**

*password - 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM*

---

### level 11 -> 12

1. `strings data.txt| tr 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz' 'NOPQRSTUVWXYZABCDEFGHIJKLMnopqrstuvwxyzabcdefghijklm`
2. `ssh -p 2220 bandit12@bandit.labs.overthewire.org`

**As the wiki states, in rot13, all the alphabets are rotated forward by 13 so tr is used to replace all the alphabets from 'A-z' to 'N-m',apllying rot13 on already rot13 encrypted data decrypts it.**

*password - JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv*

---

### level 12-> 13

**the difficulty suddenly spiked**
1.  **following the instructions in the question i made a directory in tmp**
    -  `mkdir/tmp/wow/`

2. **copied data.txt to the location**
    -  `cp ./data.txt /tmp/ wow/data.txt`

3. **since it's a hexfile, i tried to revert xxd**
    -  `xxd -r data.txt wow1`

4. **seeing 'data2.bin' in the output made me curious enough,after learning more about hexdumps i made sure to check for a file signature, seeing** `1f85`**gave me hint to 'wow1' being a gzip file and as the question mentions about the file being compressed many times**
     -  `mv wow1 wow1.gz`
     -  then i uncompress it
         -  `gzip -d wow1.gz`

    ![n1](https://github.com/oxo-crab/overthewire-bandit/blob/main/screenshot%20for%20writeup/q12_bin2.jpg)
       
5. **after running xxd through**`wow1`**i see 425a with 68 too which corrosponds to bzip version2, obviously i couldn't figure it out without** [this](https://en.wikipedia.org/wiki/List_of_file_signatures) **now on renaming it to a .bz2 file and uncompressing it again,i can move ahead.**
      -  `xxd wow1`
      -  `mv wow1 wow1.bz2`
      -  `bzip2 -d wow1.bz2`

    ![n7](https://github.com/oxo-crab/overthewire-bandit/blob/main/screenshot%20for%20writeup/q12_%201st%20bz2%20hint.jpg)

6.  **this time i see 1f85 again along with data4.bin but using the previous method gives nothing, however conerting wow1 to** `wow1.tar` **and then using tar command to unarchive gives data5.bin**
      -  `xxd wow1`
      -  `mv wow1 wow1.tar`
      -  `tar -xf wow1.tar`   -*xf is for extracting all the files*

    ![n2](https://github.com/oxo-crab/overthewire-bandit/blob/main/screenshot%20for%20writeup/q12_binn4.jpg)

7. **seeing no recognizable file signature this time around i assume it's archive again and go through the previous procedure and get**`data6.bin`
      -  `xxd data5.bin`
      -  `mv data5.bin data5.tar`
      -  `tar -xf data5.tar`
      
    ![n5](https://github.com/oxo-crab/overthewire-bandit/blob/main/screenshot%20for%20writeup/q12__%20bin6.jpg) 

8. **i notice 425a 68 again in xxd output of** `data6.bin` **i go through the procedure of step 5 again to decompress data6**
     - `mv data6.bin data6.bz2`
     - `bzip2 -d data6.bz2`
 
    ![n3]( https://github.com/oxo-crab/overthewire-bandit/blob/main/screenshot%20for%20writeup/data6%20is%20bz2%20.jpg)
9. **after running xxd through uncompressed data6 fle i see** `data8.bin` **and** `data9.bin`  **and ustar as well indicating it's archive,after the procedure we get**`data8.bin`
      - `mv data6 data6.tar`
      - `tar -xf data6.tar`

    ![n4](https://github.com/oxo-crab/overthewire-bandit/blob/main/screenshot%20for%20writeup/q_12%20tar%20file%20data8%20and%20data9%20bin%20files.jpg)

10. **after running xxd through data8.bin i see** `data9.bin` **and 1f85 header again, i convert** `data8.bin` **to** `data8.gz` **and uncompress it like usual, getting an uncompressed data8 file**
      - `mv data8.bin data8.gz`
      - `gzip -d data8.gz`

      ![n6](https://github.com/oxo-crab/overthewire-bandit/blob/main/screenshot%20for%20writeup/q12_%20data8bin%20has%20data9.jpg)

12. **upon reading data8 through strings i get the password**
      - `strings data8`

*hopefully the nextt question won't be this long, i referred to many different pages in manual and wiki for headers*

*password -> wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw*

---
### level 13 -> 14

**the private key was already shared to us in** `sshkey.private` **file, which was rsa encrypted**

**this private key was to be used to login as bandit14 to get access to** `bandit14` **file in** `/etc/bandit_pass` **as it's only readable by bandit14 user**

1.  `ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220`  -`
    -  `-i ` *is for specifying that we are logging in by using a private rsa key*
3.  `cat /etc/bandit_pass/bandit14`   


*password -fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq*

---

### level 14 -> 15

**since this time i have to access password from othern nertwork, i used** `nc` **to get the password, the hostname is** *localhost* **and the port is 3000** 

`nc localhost 3000`

**after submitting the password from previous level i get the new password**

*password - jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt*

---

### level 15 -> 16
**since we are supposed to connect using ssl encryption, we use** `s_client`, `nc` **is for raw connection**

`openssl s_client -connect localhost:30001`

*password -JQttfApK4SeyHwDlI9SXGR50qclOAil1*

---

### level  16 -> 17

**the question requires us to investigate the various ports of the server at once, so using nmap made sense**
    -  `nmap -p 3100-32000 bandit.labs.overthewire.org`
**shows 4 available ports with open state, meaning it's listening**

**i use** `openssl s_client -connect bandit.labs.overthewire.org:port` **for each port to check which one i can successfully connect to. I manage to connect to 31518 port but submitting the previous answer returnns me the same thing, meanaing this isn't the correct port. I again manage to connect to 31790, on submitting the password of previous level i get a private rsa key which i copy to my machine**'
    -  `echo '-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----' > rsakey.private`

**after logging out of the session, i get into 17th level using this private rsa key with this command** `ssh -i rsakey.private bandit17@bandit.labs.overthewire.org -p 2220` **from there i change directory** `cd etc/bandit_pass/` **and then read the password by** `cat bandit117`

*password - VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e*

