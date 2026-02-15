# Day 02 -Linux Architecture, Process, and systemd

## Linux- What is Linux?
Linux is an open source operating system based on Unix .It is widely used in servers, cloud platforms ,and DevOps environments because of its stability and security.
Most DevOps tools like Docker and Kubernetes run on Linux.


## Why Linux is used:
- **Secure**
 Linux has Strong permission and user access control. 
- **Stable**
Linux servers can run for years without reboot. 
- **Widely used**
Most cloud platforms and servers use Linux.
- **Free & Open source**
Anyone can use, modify, and distribute linux without liscence cost.
  
## Linux Architectue 

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/78e948f9-4233-4f07-9173-fa95a6372b14">

### Application 
Applications are softeware programs like browsers, editors and DevOps tools that run top of linux. 
### Shell 
The shell acts as interface between the user and the kernel, it allow the user to excecute commands like 'ls', 'pwd' and 'ps'
### Kernal
The Kernal is the core of the Linux.
It manages CPU, Memory, devices, and processes.
### Hardware 
Hardware includes physical components like CPU, RAM, disk, and network devices.


## Processes 
A process is a running instance of a program. When you execute a command or open an application, a process is created 
Each process has its owm Process Id (PID)
### Process States
 - Running – Process is using CPU
 - Sleeping – Waiting for input or resources
 - Stopped – Paused manually or by signal
 - Zombie – Process finished but not cleaned up
## Systemd 
Systemd is the dafault init system in modern linux distributions. It starts system services during boot and manages backgrund services.

# Daily Useful Linux Commands
  - ps – View running processes
  - top – Monitor CPU and memory usage
  - systemctl – Manage services
  - journalctl – View system logs
  - kill – Stop a process

# Why This Matters
 - Helps debug crashed services
 - Helps identify CPU or memory issues
 - Builds confidence in Linux troubleshooting

 






