---
title: "Tips and Tricks for Testing in Go"
date: 2025-02-17T20:07:55-06:00
tags: ["software", "engineering", "testing"]
author: "Devin Ward"
draft: false
description: ""
hideSummary: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
---

## Who this is for
Any and all writers of Go code who have the basic understanding of how to test in go. I hope that anybody from the engineer
who just finished their first test in go to the senior staff principal engineer who cannot even get close to counting the 
number of tests they have written can learn a thing or two. 

This does have concepts that apply to other programming languages too.  

## Aside
This may be the 100th unit testing presentation you have seen in your life. That is because there is still a lot 
of really bad unit test code out there (or not there which is a larger problem). The purpose of the talk is to show
things I have experienced and provide tips and comments on those. This, as all talks around this subject are, is 
opinionated. I love talking about this and enjoy somebody changing my mind. So let me know if you disagree, let's talk.

## Goal of Testing
- What is testing?
    - Testing is a broad term. Automated testing is a broad term. Unit testing is.....
    - Know that we are talking about automated testing that lives alongside your test. Majority is considered unit testing. 
    We are not here to argue or talk about this.
- Quality. Reliability. Understanding. Examples.
    - Unit testing is the single leading way to gather an understanding on what the actual code is doing. It is
    the example to your code. It should tell the reader this is what this thing does and how that behavior looks. 

## Readability - Match to Code; Not Business
- Tests as a story. 
    - We have all been there. Load up some go code. Look at some go file. And you wonder what in the hell any of this is doing? 
    README is stinky and no-good. There is little to no documentation in the code. So how do we come to understand how this thing works? 
    For me, this has come to be unit tests. They - if written well - break the code up to small pieces (by design), provide different contexts for the 
    code/system being tested to work with (more on this shortly), and should tell me exactly what is happening. 
- Match to the code; not the business.
    - My pet peeve in unit tests is helpers that do full UUID generation for a unit test. That isn't needed. It can be `00000000-0000-0000-0000-000000000001`. 
    The field called `ShipProvider` does not need to be `FedEx`; it can just be `shipper`. Two main cases where this is not true: 
    > 1. when testing code that validates a very niche business logic case - though this can potentially be a smell
    > 2. the code you are testing is intended to do something like UUID generation

    - This enables an engineer to come in and ask what the code is actually doing. It removes the confusion that business logic can sometimes create. 
    When stepping through what the code is doing, I want to know what happens when a `string` or `int` goes through this code; not a `lastName` or a `price`.

## Table/Parametrized Testing
- 99% of cases. 
    - Always and never may be curse words in this line of work, but I strongly feel that table testing should be the default approach. 
- But why?
    - Table tests or parametrized tests enable a framework that forces your test to tell a story. It forces you to walk through individual test
    cases while providing context for each. 
    - Provides scaffolding to very quickly add a new test case. When a new edge case or bug pops up, the first step in troubleshooting, debugging, and 
    ultimately fixing the bug is to add the case to the test. 

### Small Example of Table Test in Go
```Go
func TestAdd(t *testing.T) {
	// define what a test case looks like
    type testcase struct {
		name         string
		inputA       int
        inputB       int 
		expected     int
	}

    // clearly define each test case - this is where you add new cases when you find a bug or edge case
	cases := []testcase{
		{
			name:         "simple add 1 to 1",
			inputA:       1,
            inputB:       1,
			expected:     2,
		},
		// ... many more cases
	}

    // engine of test - iterate through cases and run each
	for _, tc := range cases {
		t.Run(tc.name, func(t *testing.T) {
			actual := Add(tc.inputA, tc.inputB)
			
            // use assertion library of choice to compare and report
            if actual != tc.expected {
                // problem and can fail test
            }
		})
	}
}
```

## Integration/Outsider Testing
- Unit tests belong in the same package as the code under test.
    - Using `_test` package is for integration testing. This is very useful, but is not unit testing. 
    - Aside: Unit tests in the proper package enable easier refactoring. In particular, the testing of non-exported or private 
    methods. I call this "in-the-middle" refactoring - utilizing non-exported methods to restructure code.
- Utilize proper packaging.
    - Create an `integration/` folder, place your integration tests there, and test your code as an outsider or user of your code. 
    - Very useful to test API endpoints. 

## Testing and Interfaces
- Mock away interfaces that you are not directly testing.
    - Part of the brilliance of interfaces are the ability to implement them in a mock way to enable effective testing. Implement
    them as mocks in the simplest way that still achieves the behavior and your code expects. This can be as simple as returning a string
    for some interface method like `FindBestShipProvider() string`.
- What tests tell you about interfaces
    - One of the most effective ways to realize you need an interface is when writing a test becomes overly difficult.
    Now this could be difficult for a number of reasons, BUT a common thing that continues
    to pop up in my experience is "Is the structure of this code that I am testing correct?" Often times this is felt when 
    you spend a lot of time on the set up and context generation portion of your test.
    **Example:** While writing a test I realize that I spend 15 lines preparing a struct to be tested along with an extra check at the 
    end of the test to make sure that some side-effect of the method worked appropriately. This is a sign that the code under test could
    use some work. Identify behavior, craft tests to that behavior, and rework code to fit this.

## Quick Notes on Things I have Learned
- Parallel testing
    - Please do not use `t.Parallel()` without a very specific reason. This is not the way to speed up your tests. It also does not
    reflect the state of your system in most cases. 
    - This was a particular "gotcha" in a recent role where lots of tests around the DB were utilizing parallel causing way more 
    trouble than any worth.
- AI writing tests
    - Probably my most "controversial" take. In its current state, AI has no place to write your unit tests. AI and LLMs 
    provide a statistical guess at what the code should look like piece by piece as it generates. Tests need to be deterministic.
    Even as AI approaches probable - as in the AI is right 99% of the time - solutions, I still value human input on the side of tests. 
    Maybe there is a world in which AI is writing a lot of code. In that world, I favor the workflow of the input actually being solid tests.


    The author should be the one writing unit tests to convey to any reader what the intent is. That is the purpose of tests.


    Unit tests should be a section of your code that you have the strongest understanding of. Further, it is often code that changes far 
    less than that of the code it tests. Understanding this key part of your project is important.


## TL;DR
- utilize tests as a source of understanding and intent for the code being tested
- make your code readable and extensible - utilize table/parametrized testing
- understand that tests that are hard to write are generally a smell of stinky code you are trying to test
- do put your tests in the same package as your code
- do not use `t.parallel()` unless absolutely necessary
- do not use AI to write unit tests (please)
