---
permalink: /cleancode/:title
---

Recently i had an internal discussion whether or not we should use `final` modifier on input parameters of methods.
It was hard for me to hastily gather all arguments i have against this practice. This post should clear things out.

Let's start with a simple example:
```
void print(final int score){...}  
```
What can we say about this method ? Well, for sure we can say that the `score` value cannot be changed
through the course of method `print(...)` implementation. Some may even say that it is a pretty good way to protect
against someone even trying to do such a thing. That it creates some kind of a "safety net" or documentation for
a developer using such a method.

But, there are always some "buts".. Sure it sounds great for primitive types and immutable objects, but it does not help
much in case of mutable objects and is completely redundant when using functional programming.

Goooal!! Ronaldo scores another one for his team! Time to print the new score on the score board:
```
void print(final Score score){...}
```
What guarantee do i have that the mutable object `score` won't be modified by a corrupted arbiter ?
Huh, that's easy, just read the source code! Oh.. documentation point didn't stand for long.

At least we don't have to worry that the reference to the `score` object will change!

But what if it could ?
```
void print(Score score){...}
```
Now that naughty arbiter can within `print(...)` method completely replace the reference to the `score` object.
And he does exactly that, by calling `new Score(...)` and assigning it to the `score`.
```
score = new Score(...);
```
Ronaldo is not going to win no matter what.. or is he?

Fortunately for him, he knows that **EVERYTHING IN JAVA IS PASSED BY VALUE** (references to objects also)
and the corrupted arbiter at this point has lost his last chance to change the `score` outside of method `print(...)` scope.

Reference to the object `score` inside of method `print(...)` is not the same reference as the one from outside of it.
**It is a copy** which points to the same `score` object.

#### Now about another cool feature of Java related to `final` modifier. 

In the second half of the match, the score board was replaced with a new one, which overrides `print(...)` method.
Initial method signature of the `print(...)` method was:
```
void print(final Score score){...}
```
Unfortunately overrode one looks like this:
```
void print(Score score){...}
```
Why is that ? The `final` keyword is **not** considered a part of a method signature.
That's pretty crucial in cases when you allow others to extend your code. We don't want our important `final` to get lost
along the way, don't we.. ?

Funny thing is that it's already lost on the compilation time. Decompiled `print(...)` method looks like this:
```
void print(Score score) {...}
```
Which pretty much **forces** us to download the source code every time we want to check a developer's intent.

#### _"But, but what if my method is very long and i have to be sure reference won't change ?"_
 
Keyword `final` on method input parameters was supposed to help with this issue. But it's actually only a half measure.

Whether we use an external library or we write our own - documentation is important. And there is nothing better than
a self documenting code. Clean code, which is easy to understand and validate.

If your method is very long and complex, `final` keyword won't fix your problems. It may even create that **false** feeling
of a "safety net". Which is even worse.

#### How all of this connects to the `final` on method input parameters?

(For me) It makes sense to use it only on primitive types or immutable objects. In all other cases `final` works only as a half measure.

Clean code does a lot better job at solving the same issue. So why not simply favour what is best and also improve readability
of method signatures ?

What if i told you that clean and self documenting code doesn't need such half measures ?
