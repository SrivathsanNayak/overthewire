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
Similar to natas6, this page contains an input box, a submit button and a hyperlink to view source code.
This time, the source code contains an encoded string, which on decoding will give us the password.
The secret string is encoded in the following manner: bin2hex(strrev(base64_encode($secret))).

Therefore, we have to first decode our string from hex, then reverse it, and finally decode it using base64.
Given string is 3d3d516343746d4d6d6c315669563362.
After going through the decoding process, we get "oubWYf2kBq" as the secret.
We input the secret in the input box provided, following which we get our password.
```

## Level 9

* Credentials - Username: natas9; Password: W0mMhUcRRnG8dcghE4qvk3JA9lGt8nDl; URL: <http://natas9.natas.labs.overthewire.org>

* Solution -

```markdown
The page contains an input box acting as a search function. Along with that, we have a link to view the source code.
Looking at the source code, we can discover vulnerabilities based on the code segments used.
The source code contains usage of grep as well.
Also, as the URL contains characters such as ? on submitting input query, we can attempt command injection here.
So we can try to inject different commands until we get something.
So, injecting the command ";pwd" shows us our current working directory, which is /var/www/natas/natas9
So, if we inject the command ";cat /etc/natas_webpass/natas10", it gives us the password for the next level.
```

## Level 10

* Credentials - Username: natas10; Password: nOpp1igQAkUzaI1GUUjzn1bFVj7xCNzu; URL: <http://natas10.natas.labs.overthewire.org>

* Solution -

```markdown
Similar to natas9, but this webpage informs us that it filters certain characters for security. We can check the source code here as well.
Even the code is similar to natas9, except the filter code.
Again, we can attempt command injection here by trial-and-error.
We cannot run shell commands directly, however we can do that under the pretext of searching using grep.
So commands like "a /etc/natas_webpass/natas10" would work as the letter "a" is present in the password for natas10.
So we can do similarly for natas11 using different characters until we get it.
```

## Level 11

* Credentials - Username: natas11; Password: U82q5TCMMQ9xuFoI3dYX61s7OZD9JKoK; URL: <http://natas11.natas.labs.overthewire.org>

* Solution -

```markdown
The text displays that cookies are encrypted with XOR encryption, following which there is an input to set background color using hexcodes, with a # symbol.
There is also a link to view the source code of the webpage.
The source code contains a lot of functions and we have to go through them in order to understand the logic used.
The code shows that the name of one of the cookies in the webpage has been encrypted using multiple techniques as given in the code.
The resource I'll be using for this is <https://gchq.github.io/CyberChef/>, which allows many operations for encoding and decoding.

So, first we have to find the cookie name, which is "ClVLIh4ASCsCBE8lAxMacFMZV2hdVVotEhhUJQNVAmhSEV4sFxFeaAw%3D", could be base64.
Passing it through the smart decode feature in Burp Suite, we get "ClVLIh4ASCsCBE8lAxMacFMZV2hdVVotEhhUJQNVAmhSEV4sFxFeaAw=".
We base64_decode it, getting 'UK"..H+..O%...pS.Wh]UZ-..T%.U.hR.^,..^h.'.

Also, the PHP code in source code shows that the data array processed through json_encode, xor_encrypt and base64_encode.
Therefore, we first json_encode the array, which gives us '{"showpassword":"no","bgcolor":"#ffffff"}'

Now we need to XOR the json_encode string and the base64_decode string, which gives us "qw8JAY8J]]8J\J.Jq@8Jqw8JMA8J\w.JqH8JHH8JSL."
As we can notice, the repeating string here in the key is "qw8J" with variations, which can be considered as the key.

Now, we have to again json_encode, xor_encrypt and base64_encode this string.
During xor_encrypt, we have to make a modification in our array, from "no" to "yes", i.e., the array would now be '{"showpassword":"yes","bgcolor":"#ffffff"}'.
Therefore, we do the xor_encrypt again to get the string 'UK"..H+..O%...pS.]9S[.(..W&...pST^,..^,S'.
Using base64_decode, we get "ClVLIh4ASCsCBE8lAxMacFMOXTlTWxooFhRXJh4FGnBTVF4sFxFeLFMK".

Now we can go ahead and replace the cookie data with this string, in order to get the password.
```

## Level 12

* Credentials - Username: natas12; Password: EDXp0pS26wLKHZy1rDBPUZk0RKfLGIR3; URL: <http://natas12.natas.labs.overthewire.org>

* Solution -

```markdown
```
