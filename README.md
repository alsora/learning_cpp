# Hello programming World!

I decided it was about time for me to start learning git, docker, and cpp. Let's see where this brings me!

## 0. First steps

I'm working on a Macbook. First of all, I downloaded and installed docker

https://docs.docker.com/docker-for-mac/install/

and git

https://www.atlassian.com/git/tutorials/install-git

Open a terminal to verify the installation was successful:
```bash
$ git --version
```

What I get as an output is
```bash
git version 2.15.0
```
which tells me everything is fine.

Now set your git username and email:
```bash
$ git config --global user.name "YourUserName"
$ git config --global user.email "youremail@something.com"
```
and check everything is fine by
```bash
$ git config --global user.name
```
which should result in
```bash
YourUserName
```
and the same applies to the e-mail, that is
```bash
$ git config --global user.email
youremail@something.com
```
