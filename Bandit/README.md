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

ssh bandit.labs.overthewire.org -p 2220 -l bandit5
```
