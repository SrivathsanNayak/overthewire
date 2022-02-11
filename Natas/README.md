# Natas

* In this wargame, there is no SSH login, only accessing websites by logging in using username and password.

## Level 0

* Credentials - Username: natas0; Password: natas0; URL: <http://natas0.natas.labs.overthewire.org>

* Solution -

```markdown
At first glance, there is nothing on the webpage.
If we open the console to inspect, we can see that there are a lot of tags.
The password can be found by exploring the tags further, where it is commented out.
```

## Level 1

* Credentials - Username: natas1; Password: gtVrDuiDfck831PqWsLEZy5gyDz1clto; URL: <http://natas1.natas.labs.overthewire.org>

* Solution -

```markdown
Similar to natas0, explore the console.
Right-click is not allowed, so we can use the shortcut Ctrl+Shift+I
The password can be found in a similar fashion.
```

## Level 2

* Credentials - Username: natas2; Password: ZluruAthQk7Q2MqmDeTiUij2ZvWy2mBi; URL: <http://natas2.natas.labs.overthewire.org>

* Solution -

```markdown
Initially, the webpage seems to contain no clues.
Upon inspecting, the console contains an image file linked to "files/pixel.png"
Visiting that link does not give any clue, but we can modify the URL.
By removing the "pixel.png" part, we are now in the parent directory of "files".
This contains a file with the password for natas3 in it.
```

## Level 3

* Credentials - Username: natas3; Password: sJIJNW6ucpu6HPZ1ZAchaDtwd7oGrD14; URL: <http://natas3.natas.labs.overthewire.org>
