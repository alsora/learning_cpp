# Hello programming world!

I decided it was about time for me to start learning linux, git, docker, and cpp. Let's see where this brings me!

What you find in the following can be directly applied as it is if you work on macOS, like I do.

## 1. First steps

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

Now, go to the desired folder on your pc, where you want to clone this repository. My desired folder is `Programming`, therefore what I do is
```bash
$ cd Programming
$ git clone https://github.com/ilarioazzollini/learning_cpp.git
```
which should result in the creation of a new folder `learning_cpp` (which contains everything you see in this repo), inside the desired folder `Programming`. If everything goes well, by using
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
**NOTE:** By cloning a repository you are not only downloading the current version of its content, but also its previous history.
It is also possible to just download the current version of this repo, but in this case what you will get on your machine will not be recognized by `git`.
**NOTE:**  I will not only describe how to run what you download, but how to develop the single files. In fact, I am actually writing this readme file at the same time as I am developing the code.

## 2. My first program: Hello programming world!

The idea from now on is to work on my local folder `learning_cpp` on my pc, then anytime I have some new file which I consider sort of "completed", I will push it on github. This will also hold for this `README.md` file you are currently reading. In fact, up to now I have been writing directly on the github website (like the noob I feel I am), which is not the best solution. This means my "offline" `README.md` file on my computer is not up to date. Before continuing, I solve this issue right away by opening a terminal and

```bash
$ cd Programming/learning_cpp
$ git pull
```

which results in something like

```bash
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 6 (delta 2), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), done.
From https://github.com/ilarioazzollini/learning_cpp
   e803dca..fb5b376  main       -> origin/main
Updating e803dca..fb5b376
Fast-forward
 README.md | 25 ++++++++-----------------
 1 file changed, 8 insertions(+), 17 deletions(-)
 ```

 From now on, I'm working on my local folder `learning_cpp` on my pc, and pushing any new files or modifications online to github, whenever I feel the need to do so.

 Now, I want to create a new folder inside the `learning_cpp` folder, and call it `01myfirstprogram`.

```bash
$ cd Programming/learning_cpp
$ mkdir 01myfirstprogram
```

Let's check what's inside the `learning_cpp` folder

```bash
$ ls
01myfirstprogram	LICENSE			README.md
```

Now, let's open the `01myfirstprogram` folder in visual studio code, and create a new file `hello_programming_world.cpp`

```cpp
/*
My first program in C++: Hello programming world!
I.A. Azzollini
*/

// Description: this program outputs the message "Hello programming world!" to the monitor

#include <iostream>

int main()
{
  std::cout << "Hello programming world!\n";
  return 0;
}
```

There is nothing more to be done in terms of files to be created. Next I will use docker to run an image of ubuntu 20.04 where I will compile and run the .cpp program using g++. But first I want to add, commit, and push the developed folder `01myfirstprogram` to my github. I can first check the git status of my `learning_cpp` folder (I suggest to frequently use git status)

```bash
$ cd Programming/learning_cpp
$ git status

On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	01myfirstprogram/

no changes added to commit (use "git add" and/or "git commit -a")
```

Now I can add both the modified file and the new file

```bash
$ git add README.md 01myfirstprogram
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

  modified:   README.md
	new file:   01myfirstprogram/hello_programming_world.cpp
```

Then commit everything with the attached message "My first commit from my pc", resulting in something like this

```bash
$ git commit -m "My first commit from my pc"

[main 78cb43e] My first commit from my pc
 2 files changed, 21 insertions(+), 1 deletion(-)
 create mode 100644 01myfirstprogram/hello_programming_world.cpp
```

resulting in a git status

```bash
$ git status

On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

Now we are ready to push everything online on github (github username and password will be asked)

```bash
$ git push https://github.com/ilarioazzollini/learning_cpp.git main

Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 757 bytes | 757.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/ilarioazzollini/learning_cpp.git
   9fa0bdc..78cb43e  main -> main

nothing to commit, working tree clean
```

As you can notice, the general syntax is
```bash
$ git push <url> <branch>
```

anyway, after the first push, we can simply use `git push` without specifying anything else. In this case, the local commits ready to be published, will be automatically pushed online to the last chosen url and branch (which is the current working branch).

## 3. Running the program using docker (basic usage)

First things first, what is docker? A tour to the following website is suggested

https://docs.docker.com/

We will actually follow Alberto's blog

https://alsora.github.io/2020-11-07-docker/

We want to create and run a container with ubuntu 20.04 in it. In particular, we want to run an interactive bash session, as if we were working on an ubuntu 20.04 OS. From there, we will use g++ to compile and run our program.

First, we download the docker image of ubuntu 20.04
```bash
$ docker pull ubuntu:20.04
```

Once this is completed, we create a container and run an interactive bash session by
```bash
$ docker run -it -v /Users/ilarioazzollini/Programming/learning_cpp:/root/learning_cpp ubuntu:20.04 bash
```
where we want to carry to our ubuntu session the folder `learning_cpp`. In particular we are telling docker to mount what is inside `/Users/ilarioazzollini/Programming/learning_cpp` as a volume inside the ubuntu container at location `/root/learning_cpp`.
The syntax for the command consists in using the `-v` flag followed by the host path and the container path separated by a colon.

Now you are witnessing the magic: we are in ubuntu 20.04. Let's install some basic utilities
```bash
$ apt-get update && apt-get install -y build-essential
```

Note that in a docker container you usually don't need super user permissions (`sudo`) for running commands, as the user used to access the container already has those privileges by default.

and check that the C++ compiler `g++` is now present
```bash
$ g++ --version
```

Now let's build and run the program! The source code is exactly located where we expect it to be, in fact the `learning_cpp` we have in our ubuntu image is exactly the one we prepared in macOS.
So we just compile the program by running `g++`:
```bash
$ cd root/learning_cpp/01myfirstprogram
$ g++ hello_programming_world.cpp -o output
```
and we get an executable named `output`, since that's the name that we specified.
We can run any generic executable by specifying its path in a Unix terminal, so we can simply do:
```bash
$ ./output
Hello programming world!
```

Now, we exit from this container we created, and go back to our macOS terminal by
```bash
$ exit
```

Be careful as this does not automatically means the container does not exist anymore. In fact we can always check the general docker situation by
```bash
$ docker ps -a
```
For instance what I am getting right now is
```bash
CONTAINER ID   IMAGE          COMMAND   CREATED          STATUS                          PORTS     NAMES
cf4280894278   ubuntu:20.04   "bash"    10 minutes ago   Exited (0) About a minute ago             optimistic_kilby
```
which tells me there exist one container with an ubuntu 20.04 image in it, in particular running an interactive bash.

In order to delete this container we use the command `rm` followed by the container ID, for instance in my case
```bash
$ docker rm cf4280894278
```
Now, this first part about basic usage of git and docker is done. Let's add, commit and push everything done up to here. Then we will start using both git and docker more like adults.

We open a terminal and, similarly to what we already did before, we go to our local folder, check with git status what we have changed and need to add, commit and push, and then we do that
```bash
$ cd Programming/learning_cpp
$ git status
$ git add README.md 01myfirstprogram/output
$ git commit -m "Basic usage part: completed"
$ git push
```

## 4. Running the program using docker (write your dockerfile)

First of all, let us create a new branch where we will work (and add, and commit, and push) while maintaining the main branch unchanged. This is good practice so that we may mess everything up as much as we want in our new branch, while having the last fully working version of the work safe in the main branch. It may not make much difference for this particular work, where I am working alone, but this approach helps even more when working in a team. We will create a branch, where we will develop the dockerfile, still following Alberto's blog. Only when we are sure that everything works as expected, we will create a pull request and then merge the pull request into the (upstream) main branch.

Create and switch to the new branch `ilarioazzollini/dockerfolder-branch`, and directly push it
```bash
$ cd Programming/learning_cpp
$ git checkout -b ilarioazzollini/dockerfolder-branch
$ git push
```
where git suggests to
```bash
fatal: The current branch ilarioazzollini/dockerfolder-branch has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin ilarioazzollini/dockerfolder-branch
```
which is exactly what we need to do. After doing so, we check the status
```bash
$ git status
On branch ilarioazzollini/dockerfolder-branch
Your branch is up to date with 'origin/ilarioazzollini/dockerfolder-branch'.

nothing to commit, working tree clean
```

Now let's create a new folder
```bash
$ cd 01myfirstprogram
$ mkdir basic_ubuntu_dockerfolder
```
where, following Alberto's blog, we will have a `Dockerfile`
```dockerfile
FROM ubuntu:20.04

ENV HOME /root

WORKDIR $HOME

RUN apt-get update && apt-get install -y \
    build-essential
```

together with a shell file `build.sh`
```bash
docker build -t custom_ubuntu .
```

and another shell file: the `run.sh`
```bash
docker run -it --rm -v /Users/ilarioazzollini/Programming/learning_cpp/01myfirstprogram:/root/01myfirstprogram custom_ubuntu bash
```
where, we also added the `--rm` option, in order to automatically delete the container once we exit.

Now, we could use the developed files to quickly create and run an interactive ubuntu container by
```bash
$ cd Programming/learning_cpp/01myfirstprogram/basic_ubuntu_dockerfolder
$ bash build.sh
$ bash run.sh
```
and we are in ubuntu, in particular in the root folder (as specified in the dockerfile). Exactly as before, we can run our program by
```bash
$ cd 01myfirstprogram
$ g++ hello_programming_world.cpp -o output
$ ./output
```
resulting in the same output as before
```bash
Hello programming world!
```
Now, if we exit and we check the docker situation
```bash
$ exit
$ docker ps -a
```
we get simply
```bash
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
meaning there are no open and/or active containers, as desired.

This concludes our work for now. Everything works as expected so we can push this result on github. Then, we can create a pull request and merge this branch into the main branch. Once we do that, we have to switch back to the main branch also locally on our pc, by running one by one the following commands

```bash
$ git checkout main
$ git pull
```

Now, we will go more in depth with git, linux terminal, docker, and obviously we will start cpp programming. For better organization we will work in dedicated folders, each one having its own associated readme file.