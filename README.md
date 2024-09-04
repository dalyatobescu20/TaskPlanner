# Task Scheduling System in a Datacenter

This project is a **task scheduling system** simulation for a datacenter, implemented using **Java Threads**. It allows simulating different scheduling policies, task prioritization, and preemption within a distributed computing environment.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Scheduling Policies](#scheduling-policies)
  - [Round Robin (RR)](#round-robin-rr)
  - [Shortest Queue (SQ)](#shortest-queue-sq)
  - [Size Interval Task Assignment (SITA)](#size-interval-task-assignment-sita)
  - [Least Work Left (LWL)](#least-work-left-lwl)
- [Task Properties](#task-properties)
- [Preemption](#preemption)
- [Usage](#usage)
- [Installation](#installation)
- [Testing](#testing)
- [Contributors](#contributors)
- [License](#license)

## Introduction

This project implements a **parallel and distributed task scheduler** designed for a datacenter. The system is composed of a **dispatcher (load balancer)** and multiple **compute nodes**. Tasks are dynamically allocated to nodes based on pre-defined scheduling policies. Each node manages its own task queue, executing tasks while considering task priority and preemptibility.

## Features

- **Dynamic task scheduling** using multiple policies.
- Support for task prioritization and preemption.
- Ability to handle varying numbers of nodes and tasks with different properties.
- Real-time task execution simulation with Java Threads.

## Scheduling Policies

The dispatcher can function with one of the following scheduling policies:

### Round Robin (RR)

Tasks are assigned in a round-robin fashion across nodes. The next task is assigned to node `(i + 1) % n`, where `i` is the ID of the last node assigned a task, and `n` is the total number of nodes.

### Shortest Queue (SQ)

Tasks are assigned to the node with the shortest queue, factoring in both tasks currently running and those waiting in the queue. If two nodes have equal queue lengths, the task is assigned to the node with the smaller ID.

### Size Interval Task Assignment (SITA)

Tasks are grouped into three categories based on their size (short, medium, long) and assigned to specific nodes accordingly. Each of the three nodes in this policy is dedicated to handling tasks of a particular size.

### Least Work Left (LWL)

Tasks are assigned to the node with the least amount of remaining work, calculated as the total time left to process current tasks on the node.

## Task Properties

Each task is characterized by:

- **ID**: A unique identifier.
- **Start Time**: The time at which the task enters the system.
- **Duration**: The amount of time required to complete the task.
- **Type**: Short, medium, or long (relevant for the SITA policy).
- **Priority**: Determines task importance; higher priority tasks are executed before lower priority tasks.
- **Preemptibility**: Indicates whether a task can be preempted by a higher-priority task.

## Preemption

Tasks marked as **preemptible** can be interrupted by the arrival of higher-priority tasks. Once the higher-priority task completes, the preempted task resumes execution.

## Usage

To compile and run the project, use the following commands:

```bash
$ javac *.java
$ java Main
