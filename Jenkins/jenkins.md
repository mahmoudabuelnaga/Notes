[Learn Jenkins! Complete Jenkins Course - Zero to Hero
](https://www.youtube.com/watch?v=6YZvp2GwT0A)
# Run Jenkins on Docker
> $ docker run -p 8080:8080 -p 50000:50000 --restart=on-failure -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk17

## Docker Run Options:
- Expose `port 8080`  ----> By default runs on that port.
- Expose `port 50000` ----> Master / slave communication.
- Run in `detached` mode ----> Run container in background.
- Bind `named` volume ----> Persist data of Jenkins.

## Get the password:
> $ docker ps

> $ docker logs jenkins_container_id

## Types of jenkins projects:
![alt text](<Images/Screenshot from 2024-02-21 13-00-07.png>)

# Jenkins Infrastructure Documentation

## Overview

Jenkins is a popular open-source automation server that supports building, deploying, and automating any project. A Jenkins infrastructure can vary in complexity, from a single server setup to a distributed system with multiple nodes for running jobs. This document outlines the key components and recommended practices for setting up and managing a Jenkins infrastructure.

## System Requirements

Before deploying Jenkins, ensure your system meets the following requirements:

- **Operating System**: Jenkins is cross-platform and supports Windows, Linux, macOS, and other Unix-like operating systems.
- **Java**: Jenkins requires Java to run. Supported versions include Java 8 and Java 11. It is recommended to use the latest version within these Java releases for security and performance improvements.
- **Hardware**: Minimum hardware requirements depend on the scale of your setup. A small setup (fewer than 10 jobs) can run on a system with 2 GB of RAM and 10 GB of disk space. Larger installations will require more resources.

## Installation

Jenkins can be installed using native system packages, Docker, or as a standalone application from a WAR file. Choose the method that best fits your environment and follow the official Jenkins documentation for installation instructions.

## Configuration

After installation, configure Jenkins to fit your project's needs:

1. **Secure Jenkins**: Configure security settings from "Manage Jenkins" > "Configure Global Security". Enable security, set up authentication, and define user roles.
2. **Install Plugins**: Extend Jenkins capabilities with plugins. Go to "Manage Jenkins" > "Manage Plugins". Essential plugins include Git, Pipeline, and Docker.
3. **System Configuration**: Configure system settings from "Manage Jenkins" > "Configure System". Set the number of executor threads, environment variables, and tool locations.
4. **Node Configuration**: If using a distributed setup, add and configure nodes from "Manage Jenkins" > "Manage Nodes and Clouds". Define labels, executors, and remote root directories for each node.

## Job Configuration

Create and configure jobs to automate your project tasks:

1. **Create a Job**: Click "New Item", choose a job type (e.g., Freestyle, Pipeline), and provide a name.
2. **Source Code Management**: Configure source code repositories and branches to build.
3. **Build Triggers**: Define how and when the job should be triggered (e.g., SCM poll, webhook).
4. **Build Steps**: Add steps to compile, test, or deploy your code.
5. **Post-build Actions**: Configure actions after a build, such as notifications or deploying artifacts.

## Best Practices

- **Regular Backups**: Regularly back up your Jenkins configuration and data to prevent data loss.
- **Monitoring**: Implement monitoring for your Jenkins infrastructure to track performance and detect issues early.
- **Updates**: Keep Jenkins and its plugins updated to benefit from security patches and new features.

## Scaling Jenkins

For large-scale projects, consider scaling your Jenkins infrastructure:

- **Master-Slave Architecture**: Use multiple nodes (slaves) to distribute job execution, reducing the load on the master.
- **Cloud Integration**: Integrate with cloud services for dynamic scaling of build resources.
- **Load Balancing**: Implement load balancing to distribute web interface and API requests across multiple Jenkins masters.

## Conclusion

Setting up and managing a Jenkins infrastructure requires careful planning and ongoing maintenance. By following the recommendations in this document, you can create a robust, scalable, and secure automation environment for your projects.