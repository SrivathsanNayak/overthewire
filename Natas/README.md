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

* Solution -

```markdown
Similar to natas2, this does not have any clues in the open.
However, one of the comments in the code of the website says that not even Google will help.
This is a clear reference to robots.txt, the file used by web crawlers.
So, we can check that file by appending "/robots.txt" to the URL.
This shows a hidden directory termed "/s3cr3t/".
On visiting that, we obtain the password for natas4.
```

## Level 4

* Credentials - Username: natas4; Password: Z9tkRkWmpt9Qr7XrR5jWRkgOU901swEZ; URL: <http://natas4.natas.labs.overthewire.org>

* Solution -

```markdown
Here, the message displayed on the webpage says that we are currently visiting from "http://natas4.natas.labs.overthewire.org/index.php".
On clicking the refresh link given in webpage, the URL gets updated.
We can use Burp Suite proxy to learn more about the web requests here.

Once we've started Burp Suite Proxy, we can refresh the website.
By switching the intercept on in Burp Suite, we can look at the finer details.
So, if we click on the refresh link given in the webpage, we observe that we have to login as natas5 to gain access.
In Burp Suite, it shows us that the HTTP response contains a referer field.
So, we can edit the referer field such that we are on <http://natas5.natas.labs.overthewire.org> instead of natas4.
Then, we can forward the packet and stop intercepting.
Now, we can see that it has granted us the password for next level.
```

## Level 5

* Credentials - Username: natas5; Password: iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq; URL: <http://natas5.natas.labs.overthewire.org>

* Solution -

```markdown
Webpage shows access denied as we are not logged in.
As we do not have any clues given in the webpage code, we initiate the Burp Suite application again.
Using intercept, we manage to read the GET request, which contains a parameter related to logging in.
Its current value is 0, so we change it to 1 and forward the request.
We can change the variable using the browser console too.
Upon reloading and attempting again, we get the password for natas6.
```

## Level 6

* Credentials - Username: natas6; Password: aGoY4q2Dc6MgDq4oL4YtoKtyAg9PeHa1; URL: <http://natas6.natas.labs.overthewire.org>

* Solution -

```markdown
The page contains an input box to enter a secret and a submit button.
It also contains a link to view sourcecode.
Upon clicking it, we can view the HTML code for the webpage.
It shows that the variable 'secret' is the correct query.
It also shows a link to another file called "includes/secret.inc".

Upon visiting the file, we get the following text in console "FOEIUWGHFEEUHOFUOIU".
We enter this string in the input box given in the natas6 page, which gives us the password for natas7.
```

## Level 7

* Credentials - Username: natas7; Password: 7z3hEENjQtflzgnT29q7wAvMNfZdh0i9; URL: <http://natas7.natas.labs.overthewire.org>

* Solution -

```markdown
The webpage contains nothing but two hyperlinks, Home and About.
Before going to the hyperlinks, we check the console for code.
There is a comment in the code that says the password for natas8 is in the directory /etc/natas_webpass/natas8

Now, once we visit the hyperlinks, we see that there is no special clue in both pages.
Except that these pages are in the format of index.php?page=home and index.php?page=about, respectively.
That means we can do path traversal here.
Therefore, we remove the "home" from "page=home" and add the intended directory here.
Therefore, upon visiting "/index.php?page=/etc/natas_webpass/natas8", we get the password for next level.
```

## Level 8

* Credentials - Username: natas8; Password: DBfUBfqQG69KvJvJ1iAbMoIpwSNQ9bWe; URL: <http://natas8.natas.labs.overthewire.org>

* Solution -

```markdown
```
