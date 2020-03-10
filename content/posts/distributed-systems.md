---
title: "Distributed Systems"
date: 2020-03-07T11:04:49+08:00
lastmod: 2020-03-07T11:04:49+08:00
draft: true
description: "First part of a new series. Let's learn about distributed systems!"
show_in_homepage: true
show_description: true
license: ''

tags: ["cloud", "Distributed Systems", "Today's Software"]
categories: ["Software"]

featured_image: ''
featured_image_preview: ''

comment: true
toc: false
autoCollapseToc: true
math: false
---

What are some of the thoughts and ideas that build things like AWS, GCP, and other cloud computing platforms? You have probably 
heard of concurrency, microservices, and serverless, but how do these ideas take shape? In this series, we will dive into a 
bunch of concepts in modern day software. First, we start with distributed systems.

What are distributed systems? You have probably heard the term used. How do they affect the way that we create 
software? What benefits do they provide us? Let's take a deeper look at distributed systems.

### Definition

[Wikipedia](https://en.wikipedia.org/wiki/Distributed_computing) gives the definition of a distributed system as "a system whose 
components are located on different networked computers" that "communicate and cooridinate their actions by passing messages to one 
another". The main thing here to notice is that we have some separated components, or nodes, that communicate in order to get 
some action done. This idea shouldn't be too crazy as our own human bodies are fairly complex distributed systems when you 
look internally - respiratory system, digestive system, etc.

# Overview

From the definition, we can see that we simply have some machines that communicate with each other and work together to get some goal 
done. These machines can be pretty much anything - computers, virtual machines, containers, etc. - as long as they can communicate 
with one another. These machines each work towards some common goal of the system. Think about all of the pieces of the digestive system 
in the human body. Though they all work towards the common goal of keeping the body well-nourished and clean of waste, they each 
respectively have a defined goal to get done. 

Distributed systems have three main characteristics: components fail independently of others, components run concurrently, and sharing is very limited.

### Independent Failures

Independent failures is an important part of distributed systems. It is important to keep in mind that though the components fail
independently we can still have issues with what is called **cascading failure**. This is the concept of having a component fail
that then leads to the failure of components down stream. For a great talk about this concept (along with many other great concepts),
see this [presentation](https://www.youtube.com/watch?v=CZ3wIuvmHeM).

There are many strategies with dealing with failures. It is important to keep in mind though that considering each component's
goal is to just do its defined job, we should expect a component to fail in narrowly defined ways as well. This helps leverage
some of the resiliency that distributed systems can give us.

### Concurrency

Concurrency is a major concept with distributed systems. I intend for my next article in this series to be strictly about concurrency, 
so for now let's just define it. Concurrency is the starting and running of tasks or jobs in overlapping timeframes. This *is* different 
from parallelism, but more on that in next post. 

### Sharing

In distributed systems, there is very little sharing going on between the autonomous components. Some of the main things that need 
to be kept in mind here are time, memory, and compute power. These are not shared between nodes (generally). This provides us with the 
ability to allowing each component to just committing to doing its job and nothing else. Do not need to worry about tasks overlapping 
and getting near a compute or memory limit. 

One of the main issues this causes is the need of some global way to handle some of our cross-cutting concerns. These concerns include 
things like logging, tracing, and storage.

# Benefits

- **Scalability:** Since the load is distributed across many nodes, distributed systems are very good at dealing with scale. 
*Horizontal Scaling* is an even greater benefit to distributed systems as we can create multiples of the same node if the 
load grows to that scale. 

- **Performance:** Considering we distribute the load of some job or task to an entire network of machines, we can see that 
performance will generally be better. We also have a clearer way to see when and where bottlenecks are occurring and can design 
solutions to these bottlenecks easier.

- **Reliability:** Leveraging independent node failure into a good fault-tolerant solution means that our system will be very 
reliable when distributed. If a node goes down, we can do many things such as spinning up a new node of the same kind to take the 
process and reroute the process to fall-back scenarios.

## Challenges

There are some challenges that need to be brought up when considering distributed systems.

- **Concurrency:** While concurrency is a great plus with this approach, it does need to be highlighted that it can be a problem 
if not approached properly. With this comes the problem of scheduling - how do we have our prioritized tasks run when needed? These 
decisions on when and where to run things can be difficult. Further, what happens when we are dealing with near max scale on our system 
and we have a failure. What happens to the currently running tasks? These are some things to keep in mind.

- **Latency:** As our system gets bigger and wider, we can start having issues with latency. When this becomes a large problem 
the "Choose Two Triangle" demands a choice from availability, consistency, and latency.

- **Observability:** Tracing, debugging, and logging are all some of the cross-cutting concerns mentioned earlier. With these, 
distributed systems can pose a problem with observing our applications.

# Types of Distributed Systems

- **Client-server:** Smart clients contact server for data to display to the user. When a permenant change is needed, input is sent 
to the server from the client.

- **Three-tier:** Client logic is moved to a middle layer so that there can be stateless clients. This simplifies development and 
is the architecture for most web apps.

- **n-tier:** Furthering of the three-tier architecture. This one is known for the success of application servers.

- **Peer-to-peer:** Collection of machines that can play the role of client and/or server and there are no defined task-oriented 
machines. Think bitcoin networks and BitTorrent.

# Distributed Systems in the Wild

Many things that you know and use daily are actually distributed systems. Telephone networks, the Internet, MMO games, aircraft 
control systems, and many other things are distributed systems. We use them everyday. Cloud providers that allow you to build 
applications with their services heavily rely on distributed systems. 
[Here](https://aws.amazon.com/builders-library/challenges-with-distributed-systems/) is a great post about challenges with distributed 
systems. In this article, it reads "every AWS API" is a distributed system.

# Summary

All in all, distributed systems provide us some benefits that we take advantage of nearly everyday. With proper strategies in place 
distributed systems can allow us to create performant, reliable, and scalable applications. It is also worth noting how prevelant 
this pattern is now. Any cloud provider that you can think of is built on distributed systems. The internet, telephone and cellular 
networks, MMO video games, and air traffic control systems are all things that are used everyday around us. Beyond this, many of 
the current software patterns are tending towards this - serverless and service-oriented architectures.

This post is the beginning of diving into some concepts around distributed systems, cloud computing, and similar areas. Stick 
around for more on these topics. 