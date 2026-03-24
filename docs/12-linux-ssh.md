# Linux and SSH

## Goal

The goal of this phase is to deploy a Linux server and practice remote administration using SSH.

This expands the lab environment beyond Windows and introduces cross-platform management.

---

## Environment

- DC01 — Domain Controller
- CLIENT01 — Domain Workstation
- LINUX01 — Linux Server (Ubuntu)

---

## Purpose

This phase demonstrates:

- Linux server setup
- SSH remote access
- basic Linux administration
- cross-platform networking

---

## Outcome

At the end of this phase, the lab includes a Linux system that can be accessed remotely from a Windows workstation using SSH.

---

## Additional Linux Administration Tasks

After establishing an SSH connection, additional administrative tasks were performed.

### Commands Executed

- whoami
- hostname
- pwd
- ls
- uname -a
- sudo apt update

### User Management

A new user account was created using:

sudo adduser testuser

The new account was used to test SSH login functionality.

### Concepts Learned

- Linux command-line navigation
- user account management
- package management
- remote system administration

### Result

The Linux server was successfully managed remotely from CLIENT01 using SSH, and multiple user accounts were tested.
