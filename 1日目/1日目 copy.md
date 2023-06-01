---
marp: true
theme: test
class:
  - slide
---

# AI Research Group Meeting 1

---

## Table of Contents

1. Introduction
2. SSH
3. CUI
4. Next Session Preview

---

## Introduction

The purpose of this research group is to learn practical techniques for creating AI.

The main tools that will be used and mastered are SSH, Docker, Python, and PyTorch. Specifically, these tools will be combined to remotely log in via SSH, start Docker within the remote machine, launch a JupyterLab server inside the Docker container, and enable machine learning using Python.

---

## Introduction

AI development is often mistakenly perceived as solely learning how to use machine learning libraries such as PyTorch, Keras, or TensorFlow. However, in reality, there are various other elements involved.

For example, it is rare to develop AI solely on a personal computer at home, and it is not uncommon to execute programs on school computers. However, programs can behave differently depending on the environment, so it is often surprising how seldom a program that works at home functions properly on another computer (in fact, it often results in numerous errors).

In particular, Python, while relatively straightforward in syntax, can be challenging when it comes to the development environment. Even a slight change in library or Python versions can lead to errors.

---

## Introduction

There are various reasons why programs fail to run, such as:

- Different operating systems (OS)
- Different Python versions
- Different library versions
- (In the case of machine learning) Different CUDA versions

These are just a few of the many factors to consider.

---

## Introduction

Moreover, do you go to school just to execute programs? That would be a clear waste of time. One solution to this problem is remote PC operation. Remote PC operation requires knowledge of command-based computer manipulation.

In reality, a wide range of knowledge is necessary. However, it is impossible to delve deeply into all of this knowledge. For example, explaining TCP/IP alone would require about 350 pages (as seen in the book "TCP/IP Illustrated, Volume 1"). Therefore, the approach will be to understand the minimum necessary knowledge and some additional knowledge required for practical use.

---

## SSH

SSH (Secure Shell) is a protocol used to securely log in to a remote computer. It is used to log in to a computer remotely. Let's start by reviewing SSH-related terms.

---

## Glossary (Shell, Kernel, and OS)

- An **operating system (OS)** is system software that manages computer operations. Examples include Windows, macOS, and various Linux distributions.
- **Shell** refers to the interface between the kernel and the user. It is a software.
- **Kernel** is the software that contains the necessary processing for an operating system.

---

## Glossary (IP Address, Port Number)

- An **IP address** is an address on the internet. In the past, network administrators would provide an IP address and users had to enter it into their computers to access the internet.
- Nowadays, thanks to DHCP, computers and smartphones can connect to the internet without such manual configuration as mentioned earlier.
- A **port number** is an identification number used to identify TCP/IP applications.

---

## SSH (Usage)

- For Windows users, open the Command Prompt.
- For macOS users, open the Terminal (I'm not sure since I don't have one).
- For Ubuntu and other Linux users, use Terminal.

Enter the following command:

```css
ssh -p port_number username@IP_address
```

After executing the command, the following message will appear:

```css
username@IP_address's password:
```

Enter the password as prompted.

---

## SSH (Usage)

The following screen will appear:

```ruby
hostname@username:~
```

This is the shell. The "$" sign is called the prompt and indicates that the system is ready to accept input. The default prompt is "$," but it can be changed.

By logging in this way, you can control a remote PC located far away.

To exit, enter:

```bash
exit
```

---

## Public Key Authentication and Password Authentication

What we just used is password authentication. This method is convenient because it requires minimal configuration, but it is not very secure. Public key authentication, on the other hand, is more secure. It is based on the mathematical properties of prime numbers, although the explanation would be lengthy.

Although public key authentication is secure, the setup process is a bit more complicated. In this course, we will not cover it. If you encounter a situation where you need to use it in practice, it would be best to search for instructions.

---

## CUI

CUI stands for Character User Interface, where all interactions are done through text.

Modern computers often use GUI (Graphical User Interface) and provide a graphical environment upon login. You can perform various operations using a mouse without even starting a terminal for GUI. However, even these mouse operations rely on requests made to the kernel. Considering this, the GUI environment can also be referred to as a shell that surrounds the kernel. However, in this lecture, the focus is on explaining traditional UNIX/Linux operations. So, unless specified otherwise, when we say "shell," we are referring to the CUI shell where commands are entered at the prompt.

---

## Basic Commands

1. List files and directories:`ls`
2. Display the current directory:`pwd`
3. Create a directory:`mkdir directory_name`
4. Copy a file:`cp source_file destination`

---

## Basic Commands

5. Move or rename a file:`mv source_file destination_or_renamed_file`
2. Delete a file:`rm file_name`
3. Display the contents of a file:`cat file_name`
4. Search for a specific term in the output of a command:`command | grep search_term`

---

## Next Session Preview

In the next session, we will use Docker to create a virtual environment and launch a JupyterLab server inside a container to verify if Python can be executed.