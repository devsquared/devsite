---
title: "New Series: Databases: A Deep Dive"
date: 2024-01-06T14:33:42-06:00
tags: ["software", "engineering", "Database: A Deep Dive", "series"]
author: "Devin Ward"
draft: true
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
---

-----
Quick note at the top, this is a series post. Series are longer posts with deep dives and generally have many posts in a row.
That's not for everybody. So feel free to come back for the shorter posts.
-----

Recently as I spun around in my spinny chair, I started thinking about how often I use a database and how little I 
really understood about the black box that is a database. For me and - I venture a guess - a lot of software 
engineers, we use databases constantly and really only know that it stores data and eventually learn just a passing
knowledge of SQL. So in this series we will jump in and figure it all out by first covering some basic concepts and then
implementing a couple of basic databases for ourselves.

I set out to write a run down and exploration of databases that I could not find online. Most of what I find online is either
too abstract and general or the way too complicated repo's of open sourced databases (which a great and useful but very 
difficult whenever you are just trying to learn). The other option is the often incomplete or not quite what I am looking
for blog posts from many others. I used a large combination of these compile this information. I will, of course, post
links to sources when I use them. Share the love!

## What exactly is a database? 

[Wikipedia](https://en.wikipedia.org/wiki/Database) defines a database in a bit of a confusing way. "Organized collection 
of data or type of data store" is how it starts. Then it talks quite a bit about a database management system (DBMS). It seems
that all we need to know from that is that it is the software behind the scenes that is interacting with the "end users,
applications, and the database itself to capture and analyze data". Wikipedia also then clarifies that often times the 
term "database" also loosely refers to the DBMS. We then get a bit of a treat with some sneak peaks into what exactly is 
happening - saving data to file systems, efficiency in data modeling and storage, concurrency, distributed systems, and
much, much more. These are the things we want to see in action!

Some other sources are much more succinct and to the point. [AWS](https://aws.amazon.com/what-is/database/) gives us the
simple "electronically stored, systematic collection of data" before also mentioning that the DBMS is "to store, retrieve,
and edit data". [Microsoft](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-are-databases)
goes even more general with "collection of interrelated information".

So from all of this, we have a basic understanding of what a database is and does. We have a stored collection of data
that we have some kind of management system to allow us to get to and manipulate the data.

## A quick history lesson

In the 1950s, computer programs started popping up. Most of this work was just large calculators and such. Most of the
data that came out of these machines were consumed one time and disposed of. When computers started to become commercially
available and used in the realm of business, the data began to become more and more important. Instead of reprocessing
the data every time or saving print-outs, we needed a way to save this data and re-access it.

Then in the 1960s, Charles W. Bachman designed the first DBMS. IBM responded to this with what they called the "IMS". 
These systems were the forerunners of navigational databases (more on this type of database and many more later). The 
"Database Task Group" was created by Bachman to develop what became COBOL - Common Business Oriented Language. In 1971,
this group presented the "CODASYL approach".


Bibliography for this section
D. Foote, Keith. Oct 25, 2021 - https://www.dataversity.net/brief-history-database-management/