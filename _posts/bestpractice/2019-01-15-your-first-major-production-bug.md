---
permalink: /bestpractice/:title
---

So it finally happened. You.. you the alpha and omega made a mistake. How is that even possible ?
You did everything that came to your mind. Everything should work just fine!! And yet it was not enough..

The sore feeling of defeat.. slowly munching on your confidence.

Yea, every passionate developer was there. Sad view. For some it came sooner, for some later, but it was inevitable.

## So what now ? 

First you have to accept that **you will make mistakes**! Sure, the more experience you have, the less mistakes you will make, but they will never disappear completely.

After you sober out it's the time to think about what you can do to minimize the impact.
During that phase it is important to understand that _immediately_ preparing a permanent fix might not be _the best move for NOW_.
In case of a major bug it may be required to first gain _some_ time to be able to prepare a really thought out solution.

It's highly possible you will have to make some compromises with business on how to tackle the situation to gain that precious time.
You may look for some workarounds to the problem. Majority of people understand that software engineering is a tough job and software without bugs does not really exist. 

The second most important thing you can take from this whole situation is to not make the same mistake again. Learn from it.
And to do that the first thing you should do is to replicate the bug yourself and after that write a failing test(s) to cover it.
Now fix the failing test(s)! You will not only remember this experience a lot better but you will also document your software for anyone ever facing a similar issue.

Learning on other people mistakes is always the best, but it's not always possible. Having regression tests in a project helps with that and improves maintenance a lot for anyone who will ever have to work on it.