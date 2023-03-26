---
title: "AI Writing Code"
date: 2023-03-24T14:33:42-06:00
tags: ["software", "AI", "engineering"]
author: "Devin Ward"
draft: false
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
---

AI seems to be everywhere. The super hot topic. [LLMs](https://en.wikipedia.org/wiki/Wikipedia:Large_language_models), or just generally known as AI, creeping into
software development. Will it [take our jobs](https://youtu.be/APo2p4-WXsc)?

It can be scary to think about that. Hell, the current climate around tech jobs is scary in and of itself
as the economy decides how many tech jobs the world really needs after a huge inflation during the pandemic.
And that does seem to be the use now. 

Most of these tools are being marketed as just that - tools. Or maybe more commonly referred to 
as assistants because we love to personify these AI for some reason (look at all the cute names we give them).
So should we even be worried right now?

I think there is some cause for worry, but losing our jobs isn't quite my worry.
How good are these tools? What are the plans for using them? And how much of a leash do we give them?
These are some of my questions that will be interesting to follow in the coming years. 

Also, worth noting that potentially the most interesting question is how the data collection and training will go.
There are already competing LLMs out there.
The key for these products will be how companies collect data and train off of it while trying to keep others from getting that data. 

Concerns were raised very quickly when GitHub first announced [Copilot](https://github.com/features/copilot) - marketed as "Your AI pair programmer".
Questions immediately were raised around this AI's training - "Was it any/all OSS?", "Any code stored on GitHub?", "Was it my code?".
All of this is fair to question. 

The other major question here would be which companies will benefit from this?
[Some](https://twitter.com/GergelyOrosz/status/1639286626831433729) have started to think about how larger companies 
will immediately have the leg up in the data race here. Though this isn't too out of the norm for software trends, data
is something that these companies do not and will not have a shortage of.
The impacts of how this data moating and how it is collected will be interesting to see. And could be worrying.

However, the thing that I find most interesting about this topic is how exactly it will be generally used?
Most commonly, I have heard these tools being used as some sort of templating tool. Write a prompt, take the generated code,
and modify to do the job. Others have tried to make use of it as a way to make current code better - like scanning
tests to find holes. Some have given full-fledged application ideas into some of these and let them write away.

---
<*Quick aside rant*>

One complaint that I have heard is that you can't trust the code that being generates. But that is pretty clearly silly.
First, code generators are trusted in production environments every day. Beyond that, is human written code more trustable?
What about that code that is mostly copied from Stack Overflow? Is that more trustable? This complaint is just a case of 
the fear of not having control.

<*end rant*>

---

This [tweet](https://twitter.com/ben11kehoe/status/1639355066837508096) is what got me really thinking into this. We know that 
AI at some point has a [halting problem](https://en.wikipedia.org/wiki/Halting_problem), but what about the inverse - 
halting at a proper point?

Think about a case in which a company relies on AI to do a lot of the developmental heavy lifting with a domain problem of selling
products and shipping them quickly - something akin to amazon. From an outside perspective, the answer seems to be quickly shipping
low cost products. How quickly does AI approach this solution? At which point does it decide to stop? AI has shown a proclivity 
to be good at indexing highly into certain aspects of the solution it is trying to find. Human teams and develops have already
indexed into the chosen solution and to some this is too far. Imagine what happens if AI indexes into this.

Now I understand that higher utilization of certain tools cause adjustments in how we work. If this was a problem, our
product requirements would get better. Like talking to a genie, we would figure out some way to trick it into doing what we wanted.

It seems pretty clear that we will still need a human involved in the loop. And even still, it is still
important to understand and utilize tools that are available for us to use. At the end of the day, if a tool writes all the
boilerplate code that you loathe writing for you and just needs you to review it, are you really going to say no? Would you
say no if it was available for copying and pasting from somewhere else in your codebase or Stack Overflow?