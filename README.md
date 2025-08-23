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
2. Run VirtualBox Installer
3. Verify Installation

### Step 2 : Create Virtual Machine
1. Download [Ubuntu 24.04.3 Desktop](https://ubuntu.com/download/desktop)

## Part 2: Linux Kernel Compile and Install

