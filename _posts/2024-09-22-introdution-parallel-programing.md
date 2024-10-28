---
title: "Introduction to Parallel Programing"
date: 2024-09-22
permalink: /posts/2023/08/introduction-parallel-programing/
excerpt_separator: <!--more-->
categories: parallel-programing
header:
  og_image: ""  # Replace with the path to your desired image
---

The performance of a computer is largely determined by its microprocessors. However, as the size of transistors decreases to increase speed, power consumption becomes a critical issue, most of which is dissipated as heat. Consequently, this leads to hotter integrated circuits, limiting further reductions in transistor size and performance gains. Therefore, the solution to enhance performance has shifted towards **parallelism**.<!--more--> The industry has moved from single-core to multicore processor architectures.

However, a significant challenge in this system is writing parallel code. To increase the performance of a program, the code often needs to be rewritten. Single-core computers use serial code where instructions are executed sequentially on a single core. On the other hand, parallel programming does not simply mean running the same serial code on multiple cores. In parallel programming, the code is parallelized to take advantage of multiple cores, and converting serial code to parallel can lead to entirely new algorithms.

# How Do We Write Parallel Programs?

Writing a parallel program is based on the idea of partitioning the code. Two widely used approaches are **task parallelism** and **data parallelism**:

- **Task Parallelism**: Involves partitioning tasks across different cores.
- **Data Parallelism**: Divides chunks of data across multiple cores, so cores execute the same task but with different data.

In data parallelism, three key factors are important: **communication**, **load balancing**, and **synchronization**. Different processes should communicate with each other to exchange information, and synchronization is crucial for dependencies between processes. Additionally, load balancing avoids idle time in any process. For an efficient parallel program, it is important that all cores work equally; otherwise, the power of a computer is being misused, wasting energy.

# Application Program Interfaces in Parallel Computing

The book *An Introduction to Parallel Programming* by Peter Pacheco and Matthew Malensek explores four principal APIs for parallel processing:

- **Message Passing Interface (MPI)**
- **POSIX Threads (Pthreads)**
- **OpenMP**
- **CUDA**

Each of these libraries has specific conditions for use, which include differences in memory classification and the number of independent instructions and data.

## Memory Classification

- **Shared Memory**: Cores share access to the computer's memory.
- **Distributed Memory**: Each core has its own private memory, and the cores communicate between them.

## Flynn's Taxonomy

The second condition concerns the number of instructions and data, classified according to Flynn's Taxonomy. It has four types:

- **Single Instruction Single Data (SISD)**: A single processor executes a single instruction on a single data stream. Traditional sequential computing.
- **Single Instruction Multiple Data (SIMD)**: One instruction is applied to multiple data streams simultaneously. Useful for parallel processing tasks like vector operations.
- **Multiple Instruction Single Data (MISD)**: Multiple instructions are executed on the same data stream. Rarely used in practice.
- **Multiple Instruction Multiple Data (MIMD)**: Different processors execute different instructions on different data streams. Common in modern multicore processors.

## API Applications

Each of the four libraries applies to a particular classification:

- **MPI** is applied to distributed memory MIMD systems.
- **Pthreads** is applied in shared memory MIMD systems.
- **OpenMP** is designed for shared memory MIMD and shared memory SIMD systems.
- **CUDA** is specific for NVIDIA GPUs, which have architectures involving both distributed and shared memory, SIMD, and MIMD.

## Bibliography

- Pacheco, P. S., & Malensek, M. (2021). *An Introduction to Parallel Programming* (2nd ed.). Morgan Kaufmann.
