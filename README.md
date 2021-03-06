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

The idea from now on is to work on my local folder "learning_cpp" on my pc, then anytime I have some new file which I consider sort of "completed", I will push it on github. This will also hold for this readme.md file you are currently reading. In fact, up to now I have been writing directly on the github website (like the noob I feel I am), which is not the best solution. This means my "offline" readme.md file on my computer is not up to date. Before continuing, I solve this issue right away by opening a terminal and

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

 From now on, I'm working on my local folder "learning_cpp" on my pc, and pushing any new files or modifications online to github, whenever I feel the need to do so.

 Now, I want to create a new folder inside the "learning_cpp" folder, and call it "01myfirstprogram".

```bash
$ cd Programming/learning_cpp
$ mkdir 01myfirstprogram
```

Let's check what's inside the learning_cpp folder

```bash
$ ls
01myfirstprogram	LICENSE			README.md
```

Now, let's open the 01myfirstprogram folder in visual studio code, and create a new file hello_programming_world.cpp

```cpp
// my first program in cpp
#include <iostream>

int main()
{
  std::cout << "Hello programming world! \n";
}
```

There is nothing more to be done in terms of files to be created. Next I will use docker to run an image of ubuntu 20.04 where I will compile and run the .cpp program using g++. But first I want to add, commit, and push the developed folder 01myfirstprogram to my github. I can first check the git status of my learning_cpp folder (I suggest to frequently use git status)

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

anyway, after the first push, we can simply use "git push" without specifying anything else. In this case, the local commits ready to be published, will be automatically pushed online to the last chosen url and branch (which is the current working branch).

### Running the program in Ubuntu using docker (basic usage)

First things first, what is Docker? A tour to the following website is suggested

https://docs.docker.com/

We will actually follow Alberto's blog

https://alsora.github.io/2020-11-07-docker/

We want to create and run a container with ubuntu 20.04 in it. In particular, we want to run an interactive bash session, as if we were working on an ubuntu 20.04 OS. From there, we will use g++ to compile and run our program.

First, we download the Docker image of ubuntu 20.04
```bash
$ docker pull ubuntu:20.04
```

Once this is completed, we run an interactive bash session by
```bash
$ docker run -it -v /Users/ilarioazzollini/Programming/learning_cpp:/root/learning_cpp ubuntu:20.04 bash
```
where we want to carry to our ubuntu session the folder learning_cpp. In particular we are telling docker to take what is inside /Users/ilarioazzollini/Programming/learning_cpp and bringing it inside the ubuntu container at location /root/learning_cpp.

Now you are witnessing the magic: we are in ubuntu 20.04. Let's install some basic utilities
```bash
$ apt-get update && apt-get install -y build-essential
```

and check that g++ is present
```bash
$ g++ --version
```

Now let's run the program! It's exactly located where we expect it to be, in fact the learning_cpp we have in our ubuntu image is exactly the one we prepared in macOS. So we just
```bash
$ cd root/learning_cpp/01myfirstprogram
$ g++ hello_programming_world.cpp -o output
$ ./output
```
and we get what we decided to call "output", which is indeed the output we get by running our hello_programming_world.cpp program. We should see simply
```bash
Hello programming world!
```

Now, we exit from this container (or interactive session) we created, and go back to our macOS terminal by
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

In order to delete this container we use the command "rm" followed by the container ID, for instance in my case
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

