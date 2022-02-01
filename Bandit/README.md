# Bandit

## Level 0

* Goal - The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

* Commands - ssh

* Solution -

```shell
ssh bandit.labs.overthewire.org -p 2220 -l bandit0 #enter password (bandit0)
```

## Level 1

* Goal - The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

* Commands - ls, cd, cat, file, du, find

* Solution -

```shell
ls #show list of files, in this case, readme

cat readme #show content of readme
#copy the password (boJ9jbbUNNfktd78OOpsqOltutMc3MY1)

exit #exit current ssh session

ssh bandit.labs.overthewire.org -p 2220 -l bandit1 #enter copied password
```

## Level 2

* Goal - The password for the next level is stored in a file called - located in the home directory.

* Commands - ls, cd, cat, file, du, find

* Solution -

```shell
ls

cat ./- #filename is -, copy password (CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit2
```

## Level 3

* Goal - The password for the next level is stored in a file called spaces in this filename located in the home directory.

* Commands - ls, cd, cat, file, du, find

* Solution -

```shell
ls

cat "spaces in this filename" #password (UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit3
```

## Level 4

* Goal - The password for the next level is stored in a hidden file in the inhere directory.

* Commands - ls, cd, cat, file, du, find

* Solution -

```shell
ls

cd inhere/

ls -a #shows all files, including hidden file (with prefix .)

cat .hidden #password (pIwrPrtPN36QITSp3EQaw936yaFoFgAB)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit4
```

## Level 5

* Goal - The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

* Commands - ls, cd, cat, file, du, find

* Solution -

```shell
ls

cd inhere/

ls #shows all files, we need only human-readable file

cd .. #return to parent directory

file inhere/* #shows file-type for all files inside inhere/
#shows that -file07 is human-readable

cd inhere/

cat ./-file07 #password (koReBOKuIDDepwhWk7jZC0RTdopnAYKh)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit5
```

## Level 6

* Goal - The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable, 1033 bytes in size, not executable

* Commands - ls, cd, cat, file, du, find

* Solution -

```shell
ls

cd inhere/

find . -type f -size 1033c #1033 bytes, file type, shows one file

cat ./maybehere07/.file2 #password (DXjZPULLxYr17uwoI01bNLQbtFemEgo7)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit6
```

## Level 7

* Goal - The password for the next level is stored somewhere on the server and has all of the following properties:

    owned by user bandit7, owned by group bandit6, 33 bytes in size

* Commands - ls, cd, cat, file, du, find, grep

* Solution -

```shell
ls -a #shows all files

find / -user bandit7 -group bandit6 -size 33c -type f 2> /dev/null
#here, / used to search all files and directories
#-user and -group field to search file owned by given user and group
#2> is used for stderr, so that error messages are sent to /dev/null

cat /var/lib/dpkg/info/bandit7.password #password (HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit7
```

## Level 8

* Goal - The password for the next level is stored in the file data.txt next to the word millionth.

* Commands - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

* Solution -

```shell
ls

grep millionth data.txt #shows line with the word 'millionth'
#password (cvX2JJa4CFALtqS87jk27qwqGhBM9plV)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit8
```

## Level 9

* Goal - The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

* Commands - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

* Solution -

```shell
ls

sort data.txt | uniq -uc #this will sort the file for uniq to work
#uniq -uc will give count for unique strings
#password (UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit9
```

## Level 10

* Goal - The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

* Commands - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

* Solution -

```shell
ls

strings data.txt | grep "=="
#strings filters out human-readable content
#password (truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit10
```

## Level 11

* Goal - The password for the next level is stored in the file data.txt, which contains base64 encoded data.

* Commands - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

* Solution -

```shell
ls

man base64

base64 -d data.txt #password (IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit11
```

## Level 12

* Goal - The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

* Commands - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

* Solution -

```shell
ls

tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
#translate for ROT13
#password (5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit12
```

## Level 13

* Goal - The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

* Commands - grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file

* Solution -

```shell
ls

mkdir /tmp/dir1

cp data.txt /tmp/dir1

cd /tmp/dir1

ls

xxd -r data.txt > data1 #reversing hexdump and moving output to data1

file data1 #shows that it is gzip compressed data

mv data1 data1.gz

gzip -d -k data1.gz #decompress data1.gz

file data1 #bzip2 compressed data

bzip2 -d -k data1

ls

file data1.out #gzip compressed data

mv data1.out data1.gz

gzip -dk data1.gz

file data1 #POSIX tar archive

mv data1 data1.tar

tar -xvf data1.tar #gives file named data5.bin

file data5.bin #shows that it is a tar file

tar -xvf data5.bin #gives data6.bin

file data6.bin #it is a bzip2 file

bzip2 -dk data6.bin

file data6.bin.out #tar file again

tar -xvf data6.bin.out #gives data8.bin

file data8.bin #gzip compressed file

mv data8.bin data8.gz

gzip -dk data8.gz

file data8 #ASCII text

cat data8
#password (8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit13
```

## Level 14

* Goal - The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on.

* Commands - ssh, telnet, nc, openssl, s_client, nmap

* Solution -

```shell
ls #shows sshkey.private

file sshkey.private #PEM RSA private key

ssh -i sshkey.private bandit14@localhost
#using localhost as we are already using bandit.labs.overthewire.org
#login as bandit14

cat /etc/bandit_pass/bandit14
#password (4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e)
```

## Level 15

* Goal - The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

* Commands - ssh, telnet, nc, openssl, s_client, nmap

* Solution -

```shell
nc -h #help for netcat

nc localhost 30000 #prompt for entering prev password
#password (BfMYroe26WYalil77FoDi9qh59eK5xNr)

exit

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit15
```

## Level 16

* Goal - The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption. Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

* Commands - ssh, telnet, nc, openssl, s_client, nmap

* Solution -

```shell
man openssl

openssl s_client -crlf -connect localhost:30001 -servername localhost
#connect to port 30001 on localhost using openssl
#password (cluFn7wTiGryunymYOu4RcffSxQluehd)

exit

ssh bandit.labs.overthewire.org -p 2220 -l bandit16
```
