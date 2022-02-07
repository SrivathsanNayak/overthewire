# Leviathan

## Level 0

* Goal - To login to the first level use Username - leviathan0, Password - leviathan0. Data for the levels can be found in the homedirectories. You can look at /etc/leviathan_pass for the various level passwords.

* Commands - ssh

* Solution -

```shell
ssh leviathan.labs.overthewire.org -p 2223 -l leviathan0

ls

ls -a
#shows hidden .backup directory

cd .backup/

ls

cat bookmarks.html

cat bookmarks.html | grep password
#password (rioGegei8m)

exit
```

## Level 1

* Solution -

```shell
ssh leviathan.labs.overthewire.org -p 2223 -l leviathan1

ls -a
#shows file called check

file check
#binary

./check
#asks password, tried previous password but doesn't work

strings check
#strings prints readable strings
#shows particular strings

ltrace ./check
#run a command until exits
#to understand logic used
#binary compares string with "sex"
#entering "sex" as password for binary

./check
#opens /bin/sh

whoami
#leviathan2

cat /etc/leviathan_pass/leviathan2
#password (ougahZi8Ta)

exit

exit
```
