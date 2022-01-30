# Bandit

## Level 0

* Goal - The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

* Commands - ssh

* Solution -

```shell
ssh bandit.labs.overthewire.org -p 2220 -l bandit0
```

## Level 1

* Goal - The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

* Commands - ls, cd, cat, file, du, find

* Solution -

```shell
ls #show list of files, in this case, readme

cat readme #show content of readme, copy the password from file

exit #exit current ssh session

ssh bandit.labs.overthewire.org -p 2220 -l bandit1 #enter copied password
```
