# Krypton

## Level 0

* Goal - Welcome to Krypton! The first level is easy. The following string encodes the password using Base64: S1JZUFRPTklTR1JFQVQ=. Use this password to log in to krypton.labs.overthewire.org with username krypton1 using SSH on port 2231. You can find the files for other levels in /krypton/

* Solution -

```shell
base64 --help

echo S1JZUFRPTklTR1JFQVQ= > decode.txt

base64 -d decode.txt
#password (KRYPTONISGREAT)

ssh krypton.labs.overthewire.org -p 2231 -l krypton1
```

## Level 1

* Goal - The password for level 2 is in the file ‘krypton2’. It is ‘encrypted’ using a simple rotation. It is also in non-standard ciphertext format. When using alpha characters for cipher text it is normal to group the letters into 5 letter clusters, regardless of word boundaries. This helps obfuscate any patterns. This file has kept the plain text word boundaries and carried them to the cipher text. Enjoy!

* Solution -

```shell
ls -la
#no files

ls -la /krypton/
#contains files for levels

ls -la /krypton/krypton1/
#contains 2 files

cat /krypton/krypton1/README
#instructions

cat /krypton/krypton1/krypton2
#contains ROT13 encrypted text
#YRIRY GJB CNFFJBEQ EBGGRA

tr 'A-Z' 'N-ZA-M'
#enter encrypted text
#LEVEL TWO PASSWORD ROTTEN
#password (ROTTEN)

exit
```

## Level 2

* Goal - The password for level 3 is in the file krypton3. It is in 5 letter group ciphertext. It is encrypted with a Caesar Cipher. Without any further information, this cipher text may be difficult to break. You do not have direct access to the key, however you do have access to a program that will encrypt anything you wish to give it using the key. If you think logically, this is completely easy.

* Solution -

```shell
ssh krypton.labs.overthewire.org -p 2231 -l krypton2

ls -la /krypton/krypton2
#shows files

cat /krypton/krypton2/README

cat /krypton/krypton2/krypton3
#contains encrypted password OMQEMDUEQMEK

mktemp -d

cd /tmp/tmp.RWWXXJoIOv

ln -s /krypton/krypton2/keyfile.dat
#creates symbolic link, for encrypt to run

ls -la

chmod 777 .
#full permission

/krypton/krypton2/encrypt
#use to encrypt file containing plaintext

/krypton/krypton2/encrypt /etc/issue
#trial, as given in README
#creates ciphertext file

ls -la

cat ciphertext
#has plaintext converted to ciphertext

touch testfile

vim testfile
#we can add alphabets A-Z here to see how the encrypt function works

/krypton/krypton2/encrypt testfile

cat ciphertext
#contains text from M-Z and A-L
#we can use tr to decode ciphertext

tr 'M-ZA-L' 'A-Z' < /krypton/krypton2/krypton3
#password (CAESARISEASY)

exit
```
