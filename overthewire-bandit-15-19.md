# OverTheWire: Bandit 15→19

## Bandit Level 15 → 16:

**Level Goal:** The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL encryption.

Establish a connection to the bandit15 machine. According to the level goal, we need to establish an SSL connection to the localhost on port 30001. Read the manual for openssl with the command, "man openssl".

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_20_14_59.png" alt=""><figcaption></figcaption></figure>

Following the shown syntax, establish an SSL connection through the command, "openssl s\_client localhost:30001". With this command, we establish a secure SSL connection with "s\_client" that instructs openssl to act as a client and initiate a connection to a remote server. "Localhost" is the server address we wish to connect to and "30001" is the port.

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_20_15_34.png" alt=""><figcaption></figcaption></figure>

Like in the last challenge, we need to paste and enter the password to this current level for the next level's password.

<details>

<summary>Password:</summary>

JQttfApK4SeyHwDlI9SXGR50qclOAil1

</details>

## Bandit Level 16 → 17:

**Level Goal:** The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

SSH into server bandit16, this time, we need to scan ports 31000 to 32000 to find out which ports in this range has a server listening on them. To do this, we can use nmap. Using the command "nmap localhost -p 31000-32000", we can scan the localhost from the given range to see which server will ping back.

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_20_31_47.png" alt=""><figcaption></figcaption></figure>

Next, as the level goal suggests, we need to find out which of these servers speaks SSL and which don't. Once again, use openssl to establish a connection with localhost on each port until one responds. Use the command "openssl s\_client localhost:(port)".

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_20_37_25.png" alt=""><figcaption></figcaption></figure>

Once we have established connection to the correct port, we are given an RSA private key. This is most likely our encrypted password. We can use it to log into the next level. Exit the machine, create a text file with the copied RSA text. Use the command "nano key.txt", we can use this file to log into our next machine.

Using the command "ssh bandit17@bandit.labs.overthewire.org -i key.txt -p 2220" we can attempt to connect to the server with the key in our text file on port 2220. Upon doing so we get an error that states, "It is required that your private key files are NOT accessible by others."

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_20_56_50.png" alt=""><figcaption></figcaption></figure>

Doing some research into the chmod command, we can use the code 700 so only the owner can read, write to, or execute the text file. Use the command, "chmod 700 key.txt" to change its permissions. Now again, try to establish a new ssh connection with our file.

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_20_58_10.png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Password:</summary>

```
-----BEGIN RSA PRIVATE KEY-----
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
-----END RSA PRIVATE KEY-----
```

</details>

## Bandit Level 17 → 18:

**Level Goal:** There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

As stated in the level goal, we have two files in the home directory. Since our password is the only differing string in both passwords.new and passwords.old we need to somehow find this difference.

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_21_14_50.png" alt=""><figcaption></figcaption></figure>

Upon further research, we can use the "diff" command to compare both text files. Use the command "diff passwords.new passwords.old".

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_21_27_05.png" alt=""><figcaption></figcaption></figure>

Since passwords.new was our first parameter, our password is the first line of output.&#x20;

<details>

<summary>Password:</summary>

hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

</details>

## Bandit Level 18 → 19:

**Level Goal:** The password for the next level is stored in a file **readme** in the homedirectory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.

As stated in the level goal, when trying to ssh into bandit18, we are immediately logged out. Looking up the ".bashrc" file, it is a script that is executed when a user logs into a server.&#x20;

To my knowledge, we can't modify the .bashrc file in this situation. We need to somehow read the readme file in the home directory. Looking at the ssh manual, notice that we can actually execute a command in the remote host instead of the current shell (unlike the pipe).

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_21_38_32.png" alt=""><figcaption></figcaption></figure>

This time, when typing the ssh command, append the "cat readme" command to concatenate the readme file in the home directory.

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_21_39_11.png" alt=""><figcaption></figcaption></figure>

This gives us our next password.

<details>

<summary>Password:</summary>

awhqfNnAbc1naukrpqDYcF95h7HoMTrC

</details>

## Bandit Level 19 -> 20:

**Level Goal:** To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit\_pass), after you have used the setuid binary.

After successful connection to bandit19, "ls" to see a file called "bandit20-do". For more information on the file, use the "file bandit20-do" command. We see the file is a setuid executable. Execute the file with "./bandit20-do" and we are shown that we can run a command as another use with the file.

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_22_01_00.png" alt=""><figcaption></figcaption></figure>

Knowing that the password is located in the directory, /etc/bandit\_pass/bandit20, we can cat the bandit20 password with the executable. Use the command "./bandit20-do cat /etc/bandit\_pass/bandit20" which gives us our next password.

<figure><img src=".gitbook/assets/Screenshot_2023-06-04_22_07_31.png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Password:</summary>

VxCazJaVykI6W36BkBU0mJTCM8rR95XT

</details>
