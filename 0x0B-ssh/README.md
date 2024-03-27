# 0x0B-ssh

The aim of this project is to gain proficiency in utilizing SSH (Secure Shell) and establishing connections with remote servers via SSH. SSH serves as a cryptographic network protocol facilitating secure communication between two computers. It enables secure access to a remote computer across an unsecured network, such as the internet.

## Background Context

In the realm of web development, developers frequently collaborate on remote servers hosted by third-party providers. These servers are managed by system administrators who grant developers the requisite access permissions. To access a remote server, developers rely on SSH to secure the connection between their local system and the server, ensuring secure communication.

## Learning Objectives

Upon completion of this project, learners should be able to address the following inquiries:

- What defines a server?
- Where do servers typically reside?
- What exactly is SSH?
- How does one generate an SSH RSA key pair?
- What steps are involved in connecting to a remote host using an SSH RSA key pair?
- What distinguishes SSH from other protocols?

## Repository Tasks

The project encompasses the following tasks:

#### [0. Use a private key](./0-use_a_private_key)
Gain proficiency in connecting to a server using SSH with a private key. This task entails utilizing [DigitalOcean](https://www.digitalocean.com/) for server hosting.

#### [1. Create an SSH key pair](./1-create_ssh_key_pair)
Generate an SSH key pair using `ssh-keygen`, which will be utilized for server connectivity.

#### [2. Client configuration file](./2-ssh_config)
Craft a client configuration file to streamline the SSH connection process.

#### [3. Let me in!](./3-ssh_into_your_server)
Establish connection to the server utilizing the SSH key pair generated in task 1.

#### [4. Puppet manifests](./4-puppet_ssh_config.pp)
Leverage Puppet to automate the creation of the SSH client configuration file introduced in task 2.

## How to Use

- Clone the repository to your local machine using `git clone`.
- Navigate to the directory corresponding to the desired task.
- Follow the instructions outlined in the README.md file within the respective task folder.