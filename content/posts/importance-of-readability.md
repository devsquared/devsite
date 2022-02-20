---
images:
- images/social/importance-of-readability.png
title: "Importance of Readability"
date: 2022-02-19T11:04:49+08:00
lastmod: 2022-02-19T11:04:49+08:00
draft: false
description: ""
show_in_homepage: true
show_description: true 
license: ''

tags: ['golang', 'go', 'maintainable', 'readability']
categories: ['Software']

featured_image: ''
featured_image_preview: ''

comment: false
toc: false
autoCollapseToc: true
math: false
---

*This post goes into my thoughts on Readability in code. Though it is a bit of "you know it when you see it", there are some guidelines I like to try and follow. Because I often write go, my guidelines are informed by this language but I attempt to keep it general. I am also heavily influenced by [this book by Dave Cheney](https://dave.cheney.net/practical-go/presentations/gophercon-israel.html), [Go in Practice book](https://www.manning.com/books/go-in-practice), and my experience. Obligatory "these are my opinions" and "context matters". Even with this, I hope you enjoy the read!*

When writing maintainable code, readability is the top priority. Not fewest lines of code. Not number of one-liners. Not performance. When code is easy to understand, it is easier to maintain. When code is easier to maintain, it is easier to improve. Start with focusing on readable code. Finish with code that is good in many ways likely due to many contributions from many engineers.


{{< tweet user="SanDiegoZoo" id="1453110110599868418" >}}


What really got me thinking about this was the tweet above. I think that many people underestimate the difficulty and cost in maintaining a codebase. Especially when a team loses the one or two wizards that have all of the magic to massage the system's dark and hidden unknowns. Now some of this maintainability is accomplished through other means (like testing), but I will cover this in other posts. Easing maintainability for future contributors is a must. Imagine you are told tomorrow that you are handing your project to someone else. Do you feel confident that someone else will be able to figure it out without a multi-hour walkthrough meeting?

Writing readable code is a broad and general statement. In order to try and achieve this, I first make it a goal of mine when writing. Often just thinking about the next engineer to come along and see the code helps. Then, I loosely follow these guidelines that I have put together over the years. I am sure that these guidelines - along with this post - will be updated many times. It is important to note that most of these guidelines fit more towards new code. Look out for a future posts on refactoring and the like. With that being said though, gradual progress towards these guidelines are definitely possible.

### Miscellaneous
-   Tradeoffs for readability are worth it - most of the time.
-   Above all - be consistent. If someone started the file with puns, I am sorry but follow.
-   Clarity over brevity.
-   Package names are important.

### Naming Identifiers
-   Variables should be just the correct length. Concise. Not overly complicated or overly descriptive. In this simple example, why do we need to label a map a map? Unless  context dictates we should label a map a map, don't label a map a map.
```go 
var mapOfUsers map[string]User
var users map[string]User
```

-   The larger the scope of the variable or number of usages, the larger and more descriptive the variable should be. In the silly Example 1, giving the `person` variable something like `p` is a little less readable. Whereas in Example 2, `b` as a single "branch" from the `branches` range is contained within 2 lines and used a single time. It shouldn't take too long for a reader to understand what `b` is in this context because that context is small.

Example 1:
```go
func SetupPersonForSpaceTravel(name string, age int) (Person, error) {
	person, err := NewPerson(name, age)
	if err != nil {
		return Person{}, err
	}

	person.SpaceSuitNeeded = true
	person.NeedsTraining = true
	person.IsAfraidOfSpace = false //I'd hope

	return person, nil
}
```

Example 2:
``` go
for _, b := range branches {
	traversed := append(traversed, b)
}
```

-   Context matters. In this example, we have developed an understanding of `i` as index, `x` as a simple number variable, and `n` as a limit number for repetition. Other examples are things like `db`  for database, `s` for strings, a method ending in `f` as a formatting method, and many others.
``` go
func MultiplyXBySelfNTimes(x, n int) int {
	total := 0
	for i := 0; i < n; i++ {
		total = total * x
	}

	return total
}
```
-   Variables should tell us what they contain.
-   Functions and methods should tell us what they do.


### Comments
-   The more use something gets, the more it should probably be commented.
-   Always comment public functions/methods.
-   The need to refactor is proportional to the number of comments on a part of the code. If you start writing your third paragraph of comment, it may be better to refactor it.

### Structure
- Functions should be as short as makes sense.
- Complex conditionals are better hidden in simple functions. It is easier to read something like
`if meetsCriteria()` than the 5 pieces of criteria in a line.
- Don't use naked returns.