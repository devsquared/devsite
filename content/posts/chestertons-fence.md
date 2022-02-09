---
images:
- images/social/fence-in-the-road.png
title: "A Fence in the Road"
date: 2022-02-05T11:04:49+08:00
lastmod: 2022-02-05T11:04:49+08:00
draft: false
description: "Good developers avoid cases of Chesterton's Fence; great ones know how to deal with them."
show_in_homepage: true
show_description: true
license: ''

tags: ['golang', 'go', 'maintainable']
categories: ['Software']

featured_image: ''
featured_image_preview: ''

comment: false
toc: false
autoCollapseToc: true
math: false
---

What should we do if we come across a fence in the road? Surely just remove it as it is 
blocking the way, right? Nobody in their right mind would have put a fence blocking the way.

The so-called "Prince of Paradox" gave us this [line of thinking](https://en.wikipedia.org/wiki/G._K._Chesterton#Chesterton's_fence): 

> In the matter of reforming things, as distinct from deforming them, there is one plain and simple principle; a principle which will probably be called a paradox. There exists in such a case a certain institution or law; let us say, for the sake of simplicity, a fence or gate erected across a road. The more modern type of reformer goes gaily up to it and says, 'I don't see the use of this; let us clear it away.' To which the more intelligent type of reformer will do well to answer: 'If you don't see the use of it, I certainly won't let you clear it away. Go away and think. Then, when you can come back and tell me that you do see the use of it, I may allow you to destroy it.'

## Applying this to Maintainable code

Stumbling on code that makes little sense is not abnormal for a software engineer. We often ask
“What is/was the purpose of this?". Although fruitless, we could talk about the incompetence of
the original developer. Maintainable code shouldn’t present future developers from running into
this dilemma. But how do we deal with running into this and bettering the situation?

### How to Avoid Building this Fence

The two main points I want to make here are readability and tests as documentation. I like to 
live by the philosophy that documentation (think a wiki doc) is for users and tests are for
developers. As a developer, easy to maintain code comes with tests that explain what the code is 
expected to do. 

**Strive to write readable code with even more readable tests.**

### Dealing with this Fence


We should all expect to run into this situation when working with software. Chesterton suggests going away and thinking about it. But refactoring (or, in the words of Chesterton, reforming) is about making the code better. In this situation, understanding of what is happening should be of top priority.

The first step in trying to gather understanding, we should look at the tests. In the best case, the tests will help us understand the expected behavior. In the next best case, the tests will test the logic. This actually gives us something to lean on. Refactor the code and the tests tell us if we have missed something. Even if there is some oddity while working with the tests, you will likely learn what the expected logic was.

In the case that you can’t quite understand the point with little to no tests,
a heavier refactor is needed. Tearing down the fence and forging onward may leave
logic behind. Building a bridge over the fence allows us to manage the fence in a
better way. In code, especially when we have a complex set of logic, a [facade](https://en.wikipedia.org/wiki/Facade_pattern)
is quite helpful. This facade allows us to put in place a launching point for two things:
- further exploration of what the old code is/was doing
- refactoring of the code

Make sure that when you refactor, you avoid building a new fence!

**A good developer avoids building a fence in the road; a great one knows how to deal with one**.