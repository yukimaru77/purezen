---
marp: true
theme: test
class:
  - slide
---



---

# AI Research Group Meeting 2

---

## Table of Contents

1. Recap of the Previous Session
2. Trying Out Docker
3. Launching Jupyter Lab
4. Running Python Code

---

## Recap of the Previous Session (SSH)

- SSH allows remote login to a computer.
- Required information: **IP address**, **port number**, and **username** of the remote server.
- Command: `ssh -p port_number username@IP_address`

---

## Information for SSH

| IP Address | Port Number | Username |
| --- | --- | --- |
| 133.2.194.164 | 22 | Your student ID's first character (converted to lowercase) |

---

## Review of Some Commands

| Command | Function | Syntax | Origin |
| --- | --- | --- | --- |
| ls | List files and directories | ls [directory_name] | Abbreviation of "list" |
| mkdir | Create a directory | mkdir directory_name | Abbreviation of "make directory" |
| pwd | Display the current directory | pwd | Abbreviation of "print working directory" |
| cd | Change the working directory | cd [directory_name] | Abbreviation of "change directory" |

---

## What is Docker?

Docker is an application for creating **virtual environments**. It allows the creation of virtual environments in units called **containers**. A **Docker image** serves as a blueprint for creating containers, and it can be easily distributed, enabling the creation of identical virtual environments on multiple computers.

---

## Advantages of Docker

Here are some advantages:

- Reduces the occurrence of cases where an application works on the development environment (local PC) but fails to run on a remote Linux server.
- Reduces the confusion of determining which packages are required to run an application.
- Those who have never struggled with environment-related issues are either geniuses or have no programming experience. Those who have faced environment-related challenges often find themselves turning to virtual environments, regardless of the specific application. If students can use Docker, they might gain some recognition as having experience in programming.

---

## Side Note

"Coding" refers to "creating source code using a programming language."

On the other hand, "programming" refers to "the overall process of creating a program." (However, unless someone is particularly aware, "programming" is often used to mean "coding.")

What you thought of as "programming" in Professor Chijiwa's C language class is actually "coding."

---

## Preparing for Starting a Docker Container

To create a Docker image, you need to write a Dockerfile, but since it can be a bit difficult at first, let's use a Docker image that I have prepared in advance to create a container.

As preparation, enter the following commands:

```bash
cd ~
mkdir work
```

```
cd ~` is the command to move to your home directory. Each user has their own home directory.
```

mkdir work` is the command to create a directory named "work." You will do programming in this directory from now on.

---

## Creating a Docker Container

```scss
docker run --gpus all -it --name $(whoami) --workdir /work -v $(pwd)/work:/work 
-p specified_port_number:8888 cuda1170_ubuntu1804_pytorch_is_latest bash
```

Let's explain the command.

| Option | Function |
| --- | --- |
| --gpus all | This option allows the container to access the GPU. |
| -it | Enables interactive mode. Consider it as a magic spell. |
| --name $(whoami) | Assigns a name to the container. In this case, the name will be the result of the whoami command. |

(Continued on the next page)

---

## Creating a Docker Container

```scss
docker run --gpus all -it --name $(whoami) --workdir /work -v $(pwd)/work:/work 
-p specified_port_number:8888 cuda1170_ubuntu1804_pytorch_is_latest bash
```

| Option | Function |
| --- | --- |
| --workdir /work | Specifies the working directory when the container starts as /work. |
| -v $(pwd)/work:/work | The -v option allows you to specify directories to be shared with the container. |
| -p specified_port_number:8888 | Associates the specified port number with the container's port number 8888. |

---

## Creating a Docker Container

```scss
docker run --gpus all -it --name $(whoami) --workdir /work -v $(pwd)/work:/work 
-p specified_port_number:8888 cuda1170_ubuntu1804_pytorch_is_latest bash
```

| Option | Function |
| --- | --- |
| cuda1170_ubuntu1804_pytorch_is_latest | This is the name of the Docker image I prepared. |
| bash | This is the name of the program that will be executed first when the container starts. |

---

## Getting Familiar with the Docker Container

If you executed the previous command, you should be inside the Docker container. You are logged in as a user named "root" in the Docker container (a virtual computer) using the same method as with SSH.

You can now execute commands as before. Let's create a file, for example.

```bash
echo "アメンボ青いなあいうえお" >> test.txt
```

This should create a `test.txt` file with the content "アメンボ青いなあいうえお".

```bash
cat test.txt
```

---

## Exiting from the Docker Container

You can exit the container by typing:

```bash
exit
```

This is the same as with SSH.

You can think of a Docker container as creating a computer within your computer and connecting to it via SSH.

---

## State of the Docker Container

The Docker container can be in one of the following two states:

| State | Description |
| --- | --- |
| Exited | The container exists but is not currently running. This occurs when you exit the container or stop it with the docker stop command. |
| Up | The container is currently running. This occurs when you start the container with docker run or docker start. |

To use programming terminology, both "exited" and "up" states represent instances (something that can be executed), with "up" representing an instance currently in memory and "exited" representing an instance that is not.

---

## Re-entering an Exited Docker Container

```sql
docker start container_name
```

This command brings the container back to the "up" state. After that,

```bash
docker exec -i -t container_name bash
```

allows you to enter the container via bash. Note that the container name should be your username, which is the result of the `whoami` command.

---

## Starting Jupyter Lab in the Docker Container

First, change the working directory of the Docker container to `\work`:

```bash
cd \work
```

Then enter the following command:

```css
jupyter-lab --no-browser --port=8888 --ip=0.0.0.0 --allow-root --NotebookApp.token=''
```

After that, enter the following URL in your web browser on your computer:

```arduino
http://133.2.194.164:specified_port_number/lab
```

You are now connected. If you want to stop Jupyter Lab, you can do so by pressing `Ctrl + C` in the Docker container.

---

## Running Python Code

With SSH, Docker, and Jupyter Lab, you have set up a Python execution environment.

Click "Python 3" under "Notebook" with your mouse.

This will create an ipynb file. An ipynb file allows you to interactively execute Python code and is ideal for writing disposable programs for data analysis or machine learning.

I will demonstrate the operations, but you can write your program in a cell and press `Shift + Enter` to execute the code cell.

---

## Preview of the Next Session

Next time, we will explain the basics of Python syntax and expressions and have some hands-on practice in Jupyter Lab.

---

## Supplementary Information

In fact, you don't need to use SSH to execute commands. VSCode has plugins that allow you to remotely run VSCode servers on the remote side and manipulate remote files. There are also plugins that allow you to create an interactive execution environment for Jupyter Lab directly on VSCode instead of in the web browser. Personally, I am a bit old-fashioned, and I believe that going through the slightly more cumbersome steps (even if it is painful) can be a valuable learning experience. If you can figure it out, feel free to research and try these alternative methods (which are actually quite simple).

Although I won't explain VSCode in detail this time since it's just a trial, it can be quite useful if you have the opportunity to work on AI development in your 4th year (not only in the Haruyama Lab). I encourage you to explore it.