---
title: "When to Refactor"
date: 2023-04-11T12:07:45-06:00
tags: ["software", "engineering"]
author: "Devin Ward"
draft: false
description: "Leveraging technical debt and knowing when to refactor."
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
---
---

Abstract: Many software engineers struggle with trying to fit in time to refactor and better the code - especially in environments
where a product team is driving ticketed work and features. In times of lower workload, pay off some of your tech debt; 
in times of lots of feature work, leverage tech debt. Understanding how and when to leverage technical debt is an 
important skill to have along with knowing when to pay it off. 

---

Technical debt - the need to refactor or better some code at a later point - is something that we have all come to know 
as software engineers. Our managers talk about it in our daily meetings. Our peers and us complain that we need to 
prioritize the tech debt higher while product argues for a new feature. These kind of things are pretty common in my 
experience. 

But what about leveraging this seemingly inherent part of software development?

Debt as a concept is already something that we understand when it comes to money. And it current world economy, it is 
something that we often have to utilize especially businesses and startups. Why should tech debt be any different? 

When we are low on money and need to spread out the cost of something, we often take on some debt. This can be just the
same in software work. When we are low on resources, strapped with loads of feature work, or dealing with an influx of 
customer tickets like in a peak season, we can leverage tech debt. When not in one of these cases or similar, we can then
start paying off this debt we have created. 

It is important though to think about the kind of debt created. Just the same as you would not take on debt with terrible
terms, you shouldn't create tech debt that also has terrible terms. In the context of tech debt, you shouldn't be creating
debt that is untested, not secure, or any other obvious red flags of bad code. But getting decent code out that may not 
be perfect because of some refactor or something may be good terms for you. In my experience, one thing that I have 
leveraged quite a bit is code that requires some manual steps to do something is fine; write up a runbook to outline the
steps and automations can come later. This is, per my definition, *good* technical debt.

Coming to this understanding was a big one for me. When building out software long term, tech debt is going to happen.
Understanding and working together on when to take care of it will empower dev teams to work better.