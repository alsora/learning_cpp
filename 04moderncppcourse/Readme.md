# Modern C++ Course

Now I am following the Modern C++ course 

2018 recordings: https://www.ipb.uni-bonn.de/teaching/modern-cpp/

2020 recordings: https://www.ipb.uni-bonn.de/cpp-course-2020/

together with the suggested video tutorials on how to use a linux terminal

https://www.youtube.com/watch?v=oxuRxtrO2Ag&feature=youtu.be

and pipes and redirection

https://www.youtube.com/watch?v=mV_8GbzwZMM&feature=youtu.be

From now on, we will follow the 2020 recordings of Modern C++ course.

## Setting up the dockerfile (Tutorial 0) and Lecture 0 - The Basics

By following Tutorial 0 for Linux users, we want to set up the dockerfile such that the following steps are taken, starting from a "virtual" installation of ubuntu 20.04

```bash
sudo apt update
sudo apt install build-essential clang cmake cppcheck
sudo update-alternatives --set cc /usr/bin/clang
```

In the same way as before, we create a new folder containing the `build.sh`, `run.sh`, and `Dockerfile`. In particular, the only thing that changes is the dockerfile, where we want to change the `RUN` section as

```dockerfile
FROM ubuntu:20.04

ENV HOME /root

WORKDIR $HOME

RUN apt-get update && apt-get install -y build-essential

ENV DEBIAN_FRONTEND="noninteractive" TZ="Europe/London"
RUN apt-get -y install tzdata

RUN apt-get install -y clang cmake cppcheck
```

in order to install everything we need (`cmake` needs the time zone to be set, that is why we need the extra commands related to `tzdata`). We can then check everything works fine by running one by one the following commands from the dockerfolder

```bash
$ cd dockerfolder
$ bash build.sh
$ bash run.sh
$ clang --version
$ cmake --version
$ cppcheck --version
cd 04moderncppcourse/0TheBasics
clang++ helloworld.cpp -o output
./output
exit
```

## Lecture 1 - Build and Tools

tbd...