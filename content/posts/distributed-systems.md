---
images:
- images/social/letslearndistributedsystem.png
title: "Let's Learn: Distributed Systems"
date: 2020-04-06T11:04:49+08:00
lastmod: 2020-04-06T11:04:49+08:00
draft: true
description: "First part of a new series. Let's learn about distributed systems!"
show_in_homepage: true
show_description: true
license: ''

tags: ["cloud", "Distributed Systems", "Let's Learn"]
categories: ["Let's Learn"]

featured_image: ''
featured_image_preview: ''

comment: true
toc: false
autoCollapseToc: true
math: false
---

![Let's Learn: Distributed Systems](/images/social/letslearndistributedsystem.png)

Distributed systems are a major part of the world with the current state of technology. This post aims to give a basic explanation of 
what distributed systems are and how they are used everyday from the perspective of computer science.

## What is a distributed system?

[Wikipedia](https://en.wikipedia.org/wiki/Distributed_computing)  defines a distributed system as "a system whose components ... communicate and coordinate their actions by passing messages to one another".

Simply put, a distributed system is a collection of computers working to complete a job together. This system often looks 
as if it is a single computer to an end user.

There are three key ideas about distributed system: 

 - **Shared State** - the idea that components in the system have access to some shared resources
 - **Concurrency** - the capacity for multiple tasks to run at overlapping times
 - **Independent Failures** - the ability for components to fail separately from one another

## Why a distributed system?

Distributed systems, just like everything else in the world, have pros and cons.

On the negative side of things, distributed systems tend to be complex to manage. Multiple moving parts is inherently more complex than just having a single part. Deploying these systems can also be quite a headache. Three main issue arise when talking about these systems:

 - **Task Delegation** - When and where to schedule tasks can become complex if a system is not well thought out.
 - **Latency** - As a system grows wide with many components, communication between components takes more time. This often leads to trade-offs being made in other areas.
 - **Observability** - Debugging, tracing, and logging grows to be rather tough when you have a complex distributed system. 


On a positive note, distributed systems allow for a lot of flexibility and reliability. This flexibility is realized in two main ways - scalability and performance. 

### Horizontal Scaling

Before hopping into how it helps us, let's define what horizontal scaling is. One way to scale a machine is by downloading more RAM, slapping on some more cores, or adding a coprocessor. This concept is vertical scaling - that is upgrading the hardware on a single machine. Horizontal scaling is when we add more computers to a system. 

In other words, think about a distributed system that hosts a chat between two clients. At the beginning, we only have one node that hosts this connection. If we have more clients that want to chat, the system will spin up more of the node that hosts the connection. This allows for us to distribute heavy usage on the system. 

### Breaking Up Tasks

A distributed system generally has good performance numbers because it comes with an inherent amount of efficiency. This comes from the fact that we take whatever general job that the overall system is given and break it up into smaller tasks that individual nodes take on.

For this concept, think about the human body. The general job for the body is to keep you healthy, up-and-moving, and alive. This job though is dispersed to many tasks handed to our many systems - digestive, respiratory, and cardiovascular to name a few. Even these systems have individual parts that break up the work that it is to do.

 This also allows for the components in our system to be specialized. In a similar way that we make objects in an object-oriented paradigm very focused, we too want our components of a distributed system to be focused on its task. For instance in our chat example from earlier, we may want a database to store the history of a conversation. This database though is focused on doing just that. Other components can focus on the other parts of creating a chat application.

### Reliability

One of the largest benefits from a distributed system is its reliability. The biggest reason for this is a concept called *fault tolerance*. Earlier in the article, we mentioned that distributed systems allow for individual failures. This allows for us to easily handle faults. If one of our many components finds an error, we can easily utilize our flexibility by spinning up resources to aid in resolving the issue.

For example, let's say a user of our chat application sees that their messages are not properly showing up. Somehow our component that deals with sending the messages is not working as we want it to. To solve the issue, let's just use the old trusted method of restarting the machine. In this case though, we can just spin up a new "message-sending" component and route the user their. We then just terminate the old one and life is (hopefully) good.

Their are obviously more things that come into play in the example above (log consumption, finding the error, and then fixing it so it doesn't happen again), but it explains the fault tolerance that we can expect from a distributed system. Since we have multiple machines running within our system, we can spin up and move around instances of these components as we need. This flexibility allows for great reliability.

## Examples of Distributed Systems

![Cloud Computing](/images/site/cloudCompute.png)

Distributed systems are all around us nowadays. The internet itself is a great example. Any cloud computing platform that you use (AWS, GCP, Azure, etc) are all examples. Some other notables include:

 - telecommunication networks like telephone and cellular networks
 - MMO video games
 - aircraft control systems

There are many types of distributed systems. I am not going to go into the types as I am keeping this post fairly general. But for a good starting point, check out the [wikipedia page](https://en.wikipedia.org/wiki/Distributed_computing) for it.

## Conclusion

The purpose of this article was to give a decent rundown of what a distributed system is. We looked at what concepts were involved with these systems including some of the pros and cons. We also looked at a few examples. 

If you have any thoughts or questions, let me know! 

Until next time! Cheers!

---------------------------

# Let's Learn Series

I hope that you learned at least a little something from this post. This is a part of my **Let's Learn** series. In this series, I break down a topic that I find interesting. Generally these topics are in or around the field of software, math, or computer science. If you have any ideas for a good topic, let me know! Also check out my [post](https://devsquared.space/2020/02/how-i-learn/) on how I learn, as that is how this series came to be.
