# Docker Command Cheatsheet

_Captured: 2017-03-13 at 13:53 from [dzone.com](https://dzone.com/articles/docker-command-cheatsheet?utm_source=Docker%20Bundle&utm_campaign=Monday%20Email%202017-03-13&utm_medium=email)_

Download the [Essential Cloud Buyer's Guide](https://dzone.com/go?i=123025&u=http%3A%2F%2Fpd.internap.com%2Fcloud-buyers-guide-DZ) to learn important factors to consider before selecting a provider as well as buying criteria to help you make the best decision for your infrastructure needs, brought to you in partnership with [Internap](https://dzone.com/go?i=123025&u=http%3A%2F%2Fpd.internap.com%2Fcloud-buyers-guide-DZ).

I completed the course on "[Docker Quickstart](https://linuxacademy.com/devops/training/course/name/docker-quick-start)" at LinuxAcademy recently. Throughout the course, I made some notes on the important commands I found myself using over and over again. If you are new to Docker, here are my notes on getting started with the tool.

## Installing Docker

All commands as root on CentOs7:
    
    
    baseurl=https://yum.dockerproject.com/repos/main/centos/7/
    
    
    gpgkey=https://yum.dockerproject.org/gpg
    
    
    yum install docker-engin
    
    
    usermod -a -G docker <username>
    
    
    cat /etc/group | grep docker #should use the <username> as the group for the docker program

## Docker Commands

List images:

List running docker processes:

List all processes that were ever run:

List only the container IDs:

Running processes:

Cleaning up Docker:

Redirect port:

Adding volume:

Building a Docker file:

The Cloud Zone is brought to you in partnership with [Internap](https://dzone.com/go?i=109853&u=http%3A%2F%2Fpd.internap.com%2Fbare-metal-101-pr). [Read Bare-Metal Cloud 101](https://dzone.com/go?i=109853&u=http%3A%2F%2Fpd.internap.com%2Fbare-metal-101-pr) to learn about bare-metal cloud and how it has emerged as a way to complement virtualized services.
