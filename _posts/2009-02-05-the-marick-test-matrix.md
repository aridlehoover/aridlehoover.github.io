---
layout: post
title:  The Marick Test Matrix
date:   2009-02-05 18:00
tags:   agile, testing
---
One of the leading voices in agile testing is a guy named Brian Marick. Brian is
an independent consultant and an author. I find his [blog](http://www.exampler.com/blog/)
to be an invaluable resource.

### The Marick Test Matrix

Back in 2003, Brian published an influential [series of articles on agile testing](http://www.exampler.com/old-blog/2003/08/21/#agile-testing-project-1). He was attempting to point the way forward for agile testers. But, in the process, he came up with an elegant method of cataloguing testing methods that has become known as the “Marick Test Matrix.”

I’d like to introduce the matrix here in the hopes of fostering a discussion about what we test and how we test it.

Brian’s work categorized tests by asking two questions:

1. Is the test business facing or technology facing?
2. Does the test support programming or critique a product?

When you combine the two questions (or axes), you get a grid (or matrix), like this one:

<img src="/img/posts/Marick1.png">

But, what the heck do these things mean? That’s what the remainder of this post is about&hellip;

#### Business Facing Tests

A business facing test is one that is expressed in terms that are well understood by a business expert. For example:

* If you withdraw more money than you have in your account, the system should automatically extend you a loan for the difference. (Notice that the italicized words are business terms.)

Business facing tests are best authored by people who understand the business (e.g. product owner, business analyst, etc.).

#### Technology Facing Tests

A technology facing test is one that is expressed in terms that are well understood by a technology expert. For example:

* Different browsers implement Javascript differently, so we test whether our product works with the most important ones. (Notice that the italicized words are technology terms.)

Technology facing tests are best authored by people who understand the technology (e.g. developer, tester, etc.).

#### Tests that Support Programming

A test that supports programming is one that defines what the software should do. For example:

* Clicking on the Account Details link should take the user to the Account Details screen.
* Calling the Add method with 2 and 2 should return 4.

These tests may be written before the software exists. These tests are often automated and executed after a change is made to the software to ensure that the software still works as it should (i.e. regression). Once one of these tests passes, it should never be allowed to fail again.

#### Tests that Critique a Product

A test that critiques a product is one that tries to identify problems in completed software. In other words, this is the class of tests where the tester is actively trying to break the software in order to find bugs. For example:

* When I logged on as Joe, I saw Tom’s data.
* When I clicked the blue button after clicking the red button 400 times, the system threw an error.
* When I configured the load testing tool to send 1,000 simultaneous users to the site, average response times increased to over 10 seconds.

In general, these tests are not automated – until a problem is identified, at which point an test that clearly reproduces the problem can be added to the tests that support programming.

So what?

Let’s take a look at where some standard types of testing might go on the matrix:

#### Unit Tests

Unit tests are used by developers to ensure that the code they are writing does what they expect it to. In essence, these tests form a specification for a single unit of code. By that definition, unit tests are tests that “support programming.” These tests are (or should be) very close to the code under test, which makes them “technology facing.” So, unit tests belong in the lower left quadrant of the matrix. The benefit of automating these tests is very high.

#### Functional Tests

Functional tests are used by development teams to ensure that the software they are writing does what they expect it to do. In essence, these tests form a specification for an entire system. That means that these are tests that “support programming.” But, functional tests are (or should be) written in a way that business users understand, making them “business facing.” So, functional tests belong in the upper left quadrant of the matrix. The benefit of automating these tests is high.

#### Exploratory Tests

Exploratory testing is the practice of trying to identify problems in an application. (Microsoft refers to this practice as a “Bug Bash” where many people are invited to use the software and prizes are given out to the person who identifies the most/worst bugs.) By definition, this makes these tests that “critique a product.” Exploratory tests are considered “business facing” due to the fact that the testers are using the software the same way a real end-user might. So, exploratory tests belong in the upper, right quadrant of the matrix. There is no benefit to automating exploratory tests – until a defect is identified. At that point, a new functional test can be added to ensure that the defect is resolved.

#### Performance Tests

Performance tests are used to determine the speed of an application within a specific set of parameters. Specialized tools are used to perform this testing. As such, these tests require a good deal of technical knowledge and are therefore “technology facing.” Performance tests require working software, and are therefore tests that “critique a product.” So, performance tests belong in the lower, right quadrant of the matrix.

### Putting it all together

My blog editor now tells me that I’m approaching 1000 words. So, to prove the axiom, here’s the best summary I can think of:

<img src="/img/posts/Marick2.png">

That’s enough for one day. In a subsequent post, I’ll dive into why it’s important to cover all four quadrants.

For more information, check out [Brian Marick’s original Agile Testing posts](http://www.exampler.com/old-blog/2004/05/26/#directions-toc), or [Google Marick Test Matrix](http://www.google.com/search?client=safari&rls=en&q=marik+test+matrix&ie=UTF-8&oe=UTF-8).
