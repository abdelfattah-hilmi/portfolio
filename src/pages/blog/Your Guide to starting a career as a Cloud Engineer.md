---
title: "Your Guide to starting a career as a Cloud Engineer"
excerpt: "This guide is intended for those new to cloud engineering and aims to introduce the various
skills commonly required for roles in this field."
publishDate: "2023-02-26T19:58:36.050Z"
image: "/Intro-to-cloud-from-youtube.jpg"
category: "Guides"
author: "Abdelfattah Hilmi"
layout: "@layouts/BlogLayout.astro"
tags: [Cloud, Devops, SRE]
---

This guide is intended for those new to cloud engineering and aims to introduce the various
skills commonly required for roles in this field. It's important to note that cloud-related careers
are diverse and may require different skill sets.

While certain topics and skills may be more crucial for certain career paths, it's advisable to start
by mastering the basics and then tailor your learning to your specific needs and goals.

So let’s start:


![alt text](/Intro-to-cloud-from-youtube.jpg)

## Step 1 - Operating systems:

Having a solid understanding of operating systems is an important aspect of cloud computing
and can greatly aid in the effective use and management of cloud environments. knowledge of
OSs can also be helpful when it comes to troubleshooting issues that may arise in the cloud.
Understanding how different OSs work and how to diagnose and fix common problems can help
you quickly resolve any issues that may come up. **For me** a good hands on experience with the
linux-based operating systems is a must to start your path into becoming a cloud engineer.


If you are currently using Windows 10+ you can activate the windows subsystem of linux but **I
would** advise you to switch to a linux distro of yourpreference. If you are not ready to commit to
linux as your daily drive operating system you can install it in a VM with VMware or Virtualbox,
or go with **dual boot.**

Here are some resources to guide your learning. Don’t get stuck on which distro to use, if you
do just go with **Ubuntu**.

Resources:

- Understanding what is an OS:
    [Operating Systems: Crash Course Computer Science](https://www.youtube.com/watch?v=26QPDBe-NB8)
- What are linux distros: [Choosing the Right Linux Distro](https://youtube.com/watch?v=dL05DoJ0qsQ)
    [Why so many distros? The Weird History of Linux](https://youtube.com/watch?v=dL05DoJ0qsQ)
- Installing linux on your machine:
    [How to Dual Boot Ubuntu 20.04 LTS and Windows 10](https://www.youtube.com/watch?v=-iSAyiicyQY)
- Getting familiar with linux commands:
    [The 50 Most Popular Linux & Terminal Commands - Full Course for Beginners](https://www.youtube.com/watch?v=ZtqBQ68cfJc)
- System administration basics, this is not required you can come back to this tutorial after
    learning about Networking and Distributed systems:
       [Linux Server Course - System Configuration and Operation](https://www.youtube.com/watch?v=WMy3OzvBWc0)

## Step 2 - Networking and Distributed Systems:

Networking is an important aspect of cloud engineering because it enables communication
between different devices and systems within a cloud environment. This communication is
necessary for the efficient operation of the cloud and for providing services to users.

Some benefits of networking for a cloud engineer include:


- Enabling the transfer of data between devices and systems: Networking allows cloud
engineers to transfer data between different devices and systems within the cloud
environment. This is important for tasks such as data backup, data migration, and
synchronizing data between different systems.
- Providing access to resources: Networking enables cloud engineers to provide users
with access to the resources they need, such as computing power, storage, and
applications.

- Enhancing security: Networking can be used to implement security measures such as
firewalls and encryption to protect the cloud environment and its users from cyber
threats.
- Improving scalability: Networking allows cloud engineers to easily add and remove
resources from the cloud environment as needed, improving the scalability of the cloud.
A distributed system is a collection of interconnected computers that work together as a single
system to achieve a common goal. In a distributed system, each computer is called a node and
is capable of performing a specific task or set of tasks. The nodes in a distributed system
communicate with each other through a network to share resources and information.

Distributed systems are designed to provide a number of benefits over traditional systems,
including:

- Scalability: Distributed systems can easily scale up or down by adding or removing
nodes as needed. This allows them to handle increasing workloads without performance
degradation.
- Reliability: Distributed systems are more reliable than traditional systems because they
can continue to operate even if one or more nodes fail.
- Performance: Distributed systems can often provide better performance than traditional
systems because they can divide tasks among multiple nodes and process them in
parallel.
- Flexibility: Distributed systems can be easily modified or extended by adding or removing
nodes as needed.
Examples of distributed systems include **cloud computingplatforms** , distributed databases,
and distributed file systems.

Understanding that Cloud Platforms are Distributed Systems and that Distributed systems are
basically a Network of nodes (machines) goes to show how important it is to have a solid
understanding of networking concepts.

Resources:

- Networking fundamentals series: [Intro into networking fundamentals.](https://www.youtube.com/watch?v=6hPMdpk9qA4&list=PLTk5ZYSbd9Mi_ya5tVFD8NFfU1YZOyml1&index=1)
- What is a distributed system: [Distributed Systems Introduction for Beginners](https://www.youtube.com/watch?v=MwGOjSld5iE)


## Step 3 - Automation 1 - Scripting:

Automation is a theme that you will often come across while learning cloud engineering, cloud
developers, devops engineers, SysOps admins and SREs, are all expected to manage
configuration, set up environments, manage deployments and delivery, set up monitoring and
alerts....
Different tools are used to automate these tools but we’ll have a look at them in **Automation 2** ,
in this step the requirement is to master a scripting language as it will help you reduce your
workload.
The most widely used scripting languages in cloud environments are “Bash” and “Python”, but
other viable options are “Ruby” and recently even “Golang”!

Resources:

- Bash Scripting series: [Shell Scripting Tutorial for Beginners 1 - Introduction](https://www.youtube.com/watch?v=cQepf9fY6cE&list=PLS1QulWo1RIYmaxcEqw5JhK3b-6rgdWO_)
- Python scripting project: [Learn Python Scripting With This ONE Project!](https://www.youtube.com/watch?v=dQlw1Cdd3pw)

## Step 4 - Virtualization and containerization:

This is the step you’ll find the most documentation, tutorials, and courses about, so I’ll give a
brief definition of Virtualization and containerization and leave you with the resources.

**Virtualization** involves creating a virtual machine(VM) on top of a physical host. A virtual
machine is a software emulation of a physical computer that runs on top of the host's hardware.
Each virtual machine is isolated from the other virtual machines and the host, and it has its own
operating system, applications, and data. Virtualization allows you to run multiple VMs on a
single physical host, each with its own operating system and applications. This can be useful for
testing and development, or for running multiple applications that require different operating
systems or configurations.

**Containerization** , on the other hand, involves packagingan application and its dependencies
into a container. A container is a lightweight, standalone, and executable package that includes
everything an application needs to run, including the application code, libraries, dependencies,
and runtime. Containers can be run on any host that has a container runtime, such as Docker.
Containers are isolated from each other and from the host, but they share the host's operating
system kernel. This makes containers more lightweight and efficient than virtual machines, as
they do not require a full operating system for each instance.

Keywords to go deeper than these definitions: Hypervisor, namespaces, cgroups, lxc, OCI
images.


Resources:

- Virtualization vs containerization: [Containers vs VMs: What's the difference?](https://www.youtube.com/watch?v=cjXI-yxqGTI)
- Docker series: [Docker Crash Course #1 - What is Docker?](https://www.youtube.com/watch?v=31ieHmcTUOk&list=PL4cUxeGkcC9hxjeEtdHFNYMtCpjNBm3h7&index=1)
- Docker hands-on: [Docker Tutorial for Beginners [FULL COURSE in 3 Hours]](https://www.youtube.com/watch?v=3c-iBn73dDE)
- Docker networking : [Docker networking is CRAZY!! (you NEED to learn it)](https://www.youtube.com/watch?v=bKFMS5C4CG0)
- Docker walkthrough (very important) :
    https://www.freecodecamp.org/news/the-docker-handbook/

## Step 5 - Automation 2 - Configuration management & CI/CD :

**Configuration management:**

Configuration management is the process of identifying, controlling, and maintaining the
configuration of an organization's systems and infrastructure. The goal of configuration
management is to ensure that an organization's systems and infrastructure are configured
consistently and reliably and that changes to their configuration are controlled and documented.

Configuration management involves the following activities:


- Identifying the components that make up an organization's systems and infrastructure,
and defining their configuration.
- Establishing policies and procedures for controlling and managing changes to the
configuration of these components.
- Tracking and documenting changes to the configuration of these components.
- Ensuring that the configuration of these components is consistent and reliable across
different environments, such as development, testing, staging, and production.

**Ansible:**

Ansible is a configuration management tool that can be used to automate the configuration and
management of systems and applications. With Ansible, you can define a set of instructions,
called a playbook, that specifies the desired state of your infrastructure and applications.
Ansible then executes these instructions to configure and manage your infrastructure and
deploy your applications.

Ansible provides a wide range of modules that can be used to manage and configure systems
and applications. These modules can be used to perform tasks such as installing software,
managing users and groups, managing system services, and modifying configuration files.
Ansible also provides support for a wide range of platforms and technologies, including Linux,
Windows, networking devices, cloud environments, and containerization platforms.


Ansible playbooks are written in YAML, a simple and human-readable language, and they can
be organized into roles, which are reusable collections of playbooks and tasks. This makes it
easy to define and reuse configuration management tasks across multiple systems and
environments.

Ansible is popular for its simplicity and ease of use. It uses SSH to communicate with managed
systems, so there is no need to install any agents on the managed systems. This makes it easy
to automate a wide range of tasks across multiple systems and environments.

**CI/CD:**

Continuous integration/continuous delivery (CI/CD) is a software development practice that
involves integrating code changes frequently and automatically releasing them to production.
CI/CD aims to improve the speed and reliability of software development by automating the
build, test, and deployment process. With CI/CD, developers can integrate code changes into a
shared repository, and automated tools are used to build, test, and deploy the code changes to
production. This allows organizations to quickly and frequently release new features and
updates to their applications. CI/CD helps to reduce the risk of errors and downtime, and it
allows organizations to deliver value to their customers faster.

Popular CI/CD tools include: Gitlab-CI, Jenkins, Circle Ci, Travis CI ...
**I personally only used GitlabCI so I am not in a position to compare between these
solutions.**

Resources:

- Ansible tutorial : [Getting started with Ansible 01 - Introduction](https://www.youtube.com/watch?v=3RiVKs8GHYQ&list=PLT98CRl2KxKEUHie1m24-wkyHpEsa4Y70)
- GitlabCi Crash course: [GitLab CI CD Tutorial for Beginners [Crash Course]](https://www.youtube.com/watch?v=qP8kir2GUgo)
- GitlabCi series: [Gitlab CI/CD #1 - Introduction and Architecture](https://www.youtube.com/watch?v=34u4wbeEYEo&list=PLaFCDlD-mVOlnL0f9rl3jyOHNdHU--vlJ)

## Step 6 - Focus on a Cloud provider:

So at this point I am assuming that you’ve already created an account in one or more cloud
providers and started applying what you’re learning in there. If this is the case then good stick
with the provider you’re most comfortable with and start diving deeper in the services that it
provides and try to study for an entry level or an associate certification.
Aws, Azure and GCP all offer a free tier that you can start your training with, in the case of GCP
they also have a platform called cloud skill boost that offers thousands of hands-on labs and
courses, it’s not free by default but you can reach out to any local GDSC community and they’ll
give you a renewable monthly subscription.


Resources:

- Cloud skill boost: http://cloudskillsboost.google/
- GCP Cloud digital leader:
    [Google Cloud Digital Leader Certification Course - Pass the Exam!](https://www.youtube.com/watch?v=UGRDM86MBIQ)
- GCP Associate Cloud Engineer:
    [Google Cloud Associate Cloud Engineer Course - Pass the Exam!](https://www.youtube.com/watch?v=jpno8FSqpc8)
- AWS Cloud Practitioner:
    [AWS Certified Cloud Practitioner Certification Course (CLF-C01) - Pass the Exam!](https://www.youtube.com/watch?v=SOTamWNgDKc)
- AWS Solution Architect Associate:
    [AWS Certified Solutions Architect - Associate 2020 (PASS THE EXAM!)](https://www.youtube.com/watch?v=Ia-UEYYR44s)

## Step 7 - Infrastructure As Code:

Infrastructure as code (IaC) is a software development practice that involves managing
infrastructure, such as servers, networks, and cloud resources, using code and configuration
files. IaC allows organizations to define, provision, and manage infrastructure using automated
tools and processes, rather than manually configuring infrastructure using a graphical user
interface or manual processes.

**Terraform:**
Terraform is an open-source tool for building, changing, and versioning infrastructure safely and
efficiently. It is a tool for infrastructure as code (IaC) that allows you to define infrastructure using
code and configuration files, and then use those files to provision and manage infrastructure
across a variety of providers, including cloud providers, on-premises environments, and
third-party services. Terraform provides a range of features for building, changing, and
versioning infrastructure, including support for a wide range of platforms and technologies, and
it allows you to automate the provisioning and management of infrastructure.

Resources:

- What is terraform: [Terraform explained in 15 mins | Terraform Tutorial for Beginners](https://www.youtube.com/watch?v=l5k1ai_GBDE)
- The official documentation is awesome 👏👏:
    https://developer.hashicorp.com/terraform/docs

## Next Steps:

- Learning Orchestration: Kubernetes ecosystem / Docker Swarm.
- Specializing in a cloud related role.
  
-> Stay tuned, these guides are coming soon.
