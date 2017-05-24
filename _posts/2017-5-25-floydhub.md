---
layout: post
title: Train Deep Learning models in the cloud, (No credit card required)
published: true
date: May 24, 2017
read_time: 1m
---
I was working on my Deep Learning assignment that needed me to train Resnet50 over a dataset, I was provided with a GPU machine for it. However the login credentials iven by me were given to many other students also and this lead to chaos on that machine. No code could run reliably, there is no guarantee that the process will get to live. Most processes were killed prematurely by other users.  
It was clear that I needed a different machine, but being an Indian I wanted it for free. ENTER Floydhub! 

## Floydhub  
Floydhub is the Heroku of DL, it uses Amazon AWS as back end and provides 100 hours of free GPU usage, that too an NVIDIA Tesla K80! User just needs to install floydhub-cli client and register using email address. There is also support for Jupyter notebooks, That is DOPE!  
## Usage
After installation of floyd-cli client and authentication, goto project folder and run the following commands:
floyd init PROJECT_NAME
floyd run --gpu "python FILE.py"  (replace with --cpu for CPU instance)

To launch a Jupyter server
floyd run --mode jupyter --gpu
