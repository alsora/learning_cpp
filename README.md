# Hello programming World!

I decided it was about time for me to start learning git, docker, and cpp. Let's see where this brings me!

## 0. First steps

I'm working on a Macbook. First of all, I downloaded and installed docker

https://docs.docker.com/docker-for-mac/install/

and git

https://www.atlassian.com/git/tutorials/install-git

Open a terminal to verify the installation was successful by
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

Now, go to the desired directory on your pc, where you want to clone this repository. My desired folder is "Programming", therefore what I do is
```bash
$ cd Programming
$ git clone https://github.com/ilarioazzollini/learning_cpp.git
```
which should result in the creation of a new folder "learning_cpp" (which contains everything you see in this repo), inside the desired folder "Programming". If everything goes well, by using
```bash
$ cd learning_cpp
$ git status
```
you should get
```bash
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```
## 1. The docker folder

What is docker, you ask? You can find a clear overview in Alberto's blog

https://alsora.github.io/2020-11-07-docker/

Now we are ready to start using it...
