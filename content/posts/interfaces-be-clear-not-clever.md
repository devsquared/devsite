---
title: "Interfaces: Be Clear Not Clever"
date: 2025-02-26T20:39:40-07:00
# weight: 1
# aliases: ["/first"]
tags: ['golang', 'go', 'maintainable', 'readability']
author: "Devin Ward"
draft: true
description: ""
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
---

> Abstract:
> A lot of software engineers struggle with creating clean and effective interfaces
> quickly. Early in my career, I struggled with this quite a lot. I would find myself
> trying to start coding but wanting some interface to aid in the modelling of the
> solution to some problem. What changed for me was a realization of the application 
> of a well-known [go proverb](https://go-proverbs.github.io/) - "Clear is better than clever.
> In clearer terms: when the interface is clear and evident, make it; when it is not so clear,
> don't try to be clever and create something that may not need be there. If you cannot figure
> out the interface immediately, go about coding the solution. If an interface is needed, you 
> will find it in time.

- talk about the struggle for engineers of all levels to find and create good interfaces
- talk about the go proverb: clear not clever
- brings those together in a talk about when an interface is clear - 
whether through the duplication of code OR just the presence of clearly defined
behavior