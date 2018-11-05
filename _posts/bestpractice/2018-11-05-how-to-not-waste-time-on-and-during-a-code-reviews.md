---
permalink: /bestpractice/:title
---

# Few best practices gathered over the years

Let's be honest, programmers that care about quality of their work know that code reviews are highly beneficial for it.
Reasons are plentiful, code reviews:

- improve code quality ( readability, design and coverage )
- serve as a medium to share knowledge ( both ways )
- decrease number of bugs at an early stage ( when it's easy to fix them )
- decrease development time of a project
- improve communication in a team ( f2f )

And many more.

Unfortunately, doing a good code review takes a lot of time. Especially when you don't have a lot of experience.
To help some of you ( newer developers ) who are looking for some tips about how to not waste time on and during a code review,
here are a few best practices i've gathered over the years.

## Predefine Code Review Requirements

In my current TT team (2018) we have a check list which describes requirements which someone has to pass before even asking for a code review.
There is no point wasting someone's time if those requirements are not met.

The list is as follows:

* Code is formatted using agreed on formatter
* Code conforms to team style guidelines
* Code conforms to team security guidelines
* Code conforms to company guidelines ( in special cases like Branding etc. )
* Code compiles
* Code passes all automated test suites
* Number of code lines to review is small enough ( max 300 lines and in case of bigger features those are cut into PRs thematically: API/API Documentation/Service Layer/Model etc. )

And one additional requirement we have ( mostly for documentation purposes ):

* Commits have a reference to detailed description ( in our case - ticket numbers )

Some of those points can be easily automated via IDE checkstyle or Pull Request pipeline, which even further simplify the task.

## Code Review

After all requirements for code review are met you can finally dive into it. Beside obvious things like business logic correctness, readability, design, language best practices etc.. Again, to not waste own or someone else's time there are few things to watch out for, like:

* Being polite - It might sound funny, but if you gonna be a dick to someone, he/she will most likely respond in the same manner. That's just a recipe for disaster. The nicer you are the faster you will get feedback or your remarks will be applied.
* Taking a good look at tests -  Tests are a software documentation. If tests make no sense or are missing corner cases, it's better to ping-pong the PR. It's highly possible that after reviewee updates the tests, rest of the PR will change significantly.
* Unknown to you libraries -  If you are not familiar with them, ask for explanation. Don't blindly accept changes ( this is also a great opportunity to learn something new ).
* Finding something really stupid - Don't react with famous "WTF IS THIS SHIT". Instead give constructive feedback and propose solutions.
* Finding something that is not straightforward, but for w/e reason cannot be changed - At least ask reviewee to document that ( think about future maintenance ).
* Making breaks between review sessions - You will get tired fast.. Going through someone else's code is a lot less exciting than writing something yourself. The more tired you are the worse your code review quality becomes.

That's it. Mind what you have learned. Save you it can.