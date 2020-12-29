# Hello programming world!

I decided it was about time for me to start learning git, docker, and cpp. Let's see where this brings me!

What you find in the following can be directly applied as it is if you work on macOS, like I do.

## 00. First steps

First of all, I download and install docker

https://docs.docker.com/docker-for-mac/install/

git

https://www.atlassian.com/git/tutorials/install-git

and Visual Studio Code

https://code.visualstudio.com/

Open a terminal to verify the git installation was successful by
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
$ git config --global user.name "USERNAME"
$ git config --global user.email "email@something.com"
```
and check everything is fine by
```bash
$ git config --global user.name
```
which should result in
```bash
USERNAME
```
and the same applies to the e-mail, that is
```bash
$ git config --global user.email
email@something.com
```

Now, go to the desired folder on your pc, where you want to clone this repository. My desired folder is "Programming", therefore what I do is
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
**NOTE:** What you clone is obviously the final product (or, at least, the current version) of my work. In the following, I will not only describe how to run what you download, but how to develop the single files. In fact, I am actually writing this readme file at the same time as I am developing the code.

## 01. My first program: Hello programming world!

The idea from now on is to work on my local folder "learning_cpp" on my pc, then anytime I have some new file which I consider sort of "completed", I will push it on github. This will also hold for this readme.md file you are currently reading. In fact, up to now I have been writing directly on the github website, which is not the best solution. This means my "offline" readme.md file on my computer is not up to date. Before continuing, I solve this issue right away by opening a terminal and

```bash
$ cd Programming/learning_cpp
$ git pull
```

which results in...
