# CS5204-Fall2025 Instruction

Welcome to the Fall 2025 CS5204 Operating Systems course!

This semester, you will be completing three major projects designed to give you hands-on experience with core operating system concepts. These projects are an essential part of the curriculum and will challenge you to apply the theoretical knowledge you gain in lectures.

The projects will be published sequentially on the course GitHub repository as the semester progresses. Due dates for each project will be announced later.

Here are the three projects for the semester:

- **Project 1: Filesystem Checker**

This project will involve writing a utility to check the consistency of a simulated filesystem. You'll need to understand and work with on-disk data structures, such as inodes, directory entries, and free block maps, to identify and fix common filesystem errors.

- **Project 2: Memory Page Table Walk**

In this project, you will implement and analyze the page table walk within a simulated operating system. You will explore how virtual address translation is managed differently at the user level and the kernel level.

- **Project 3: Concurrency Web Server**

The final project will focus on concurrency and synchronization. You will build a multi-threaded web server capable of handling multiple client requests simultaneously.


# Project 0

Before starting the main projects, you will first complete Project 0, which focuses on setting up your development environment. A consistent and properly configured environment is critical for systems programming, especially when working with low-level OS concepts.

## Part 1: Virtual Machine Setup

To provide a consistent environment across all students, we recommend using the course-provided Linux virtual machine (VM).

*Note: If you already have access to a reliable Linux environment and are comfortable using it for kernel development, you may skip this step. However, be aware that all grading and testing will be performed inside the course VM. If your custom environment behaves differently, it will be your responsibility to resolve any discrepancies.*

### Step 1 : Install Oracle VirtualBox
1. Download [VirtualBox](https://www.virtualbox.org/)
   + Note: You can also use other VM machine (e.g. VMWare)
2. Run VirtualBox Installer
3. Verify Installation

### Step 2 : Create Virtual Machine
1. Download [Ubuntu 24.04.3 Desktop iso file](https://ubuntu.com/download/desktop)
2. Create a New Virtual Machine
   + Click **New** (top menu)
   + Name: `CS-5204-YourName`
   + ISO Image: Downloaded ubuntu iso image
3. Specify Virtual Hardware
   + Memory (RAM): At least 4GB (8GB recommended)
   + CPUs: At least 2 CPU (more if available)
   + Disk: At least 50 GB
4. Install Ubuntu
5. Verify Installation
   + One installation completes, reboot the VM
  
### Step 3: Configure the VM
1. Update the System
````
sudo apt update
sudo apt upgrade
````
2. Install Essential Packages
```
sudo apt install -y build-essential git wget curl flex bison libncurses-dev libssl-dev vim
```
...and some other packages you want to install

3. Create a Snapshot
   + In VirtualBox Manager, select VM -> Snapshots -> Take Snapshot
   + You can use this snapshot as a restore point

## Part 2: Linux Kernel Compile and Install

Now that your Ubuntu VM is ready, the next step is to gain hands-on experience by compiling the Linux kernel from source. In this lecture, we will use *linux kernel 6.14*.

### Step 1: Download and Unzip Kernel Source
1. Get Linux Kernel 6.14 tar file
```
wget https://www.kernel.org/pub/linux/kernel/v6.x/linux-6.14.tar.xz
tar xvf linux-6.14.tar.xz
cd linux-6.14
```
2. Install Packages for Kernel Build
```
sudo apt-get install -y vim make gcc bc libelf-dev dwarves fakeroot pahole ccache libdw-dev gawk
```
3. Configure the Kernel
   + Copy the default kernel config file
     ```
     cp /boot/config-$(uname -r) .config
     ```
   + Update the configuration
     ```
     make menuconfig
     ```
     Just click \<load\> \<save\> \<exit\>
4. Compile and Install the Kernel
   + Before start compile the kernel, you may do this
     ```
     scripts/config --disable SYSTEM_TRUSTED_KEYS
     scripts/config --disable SYSTEM_REVOCATION_KEYS
     ```
   + Now compile and install the kernel
     ```
     make -j$(nproc) && make modules -j$(nproc) && sudo make INSTALL_MODE_STRIP=1 modules_install -j$(nproc) && sudo make install -j$(nproc)
     ```
     This may take long time (like 1~2 hours), so please never turn off the VM until it finished
   + Reboot the VM
     ```
     reboot now
     ```
   + Check Kernel Version
     ```
     uname -r
     ```
     If it shows, `kernel-6.14,` you are good to go
