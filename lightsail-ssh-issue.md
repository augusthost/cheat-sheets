After I was able to ssh via Google web console, I did the following steps to resolve this:

Generate ssh key using `ssh-keygen`

Copy the key.pub file contents

Append the contents to `~/.ssh/authorized_keys` file

`sudo nano ~/.ssh/authorized_keys`
