---
permalink: /cleancode/:title
---

## Going a little back in time

When i started my first job as a software developer i didn't really pay much attention to the quality of the code but rather if it simply does what it should.
The amount of work didn't really help with that either - we were always behind the schedule. Ofcourse there were "code reviews" but looking back those were not really well executed.
Composition of the team at the time was: two juniors, one tester, two regulars and one lead. Feature after feature, bugfix after bugfix, tests, deployment and repeat kind of job.

In the end everything "did what it should" but each next iteration was longer. Modifications were more painful to introduce and fixing bugs uhg, you probably know where im heading to..
Around that time my fellow junior teammate borrowed me the Clean Code by Uncle Bob. So i read it in between lectures and exchanged my thoughts with him afterwards.
We both loved to code so our next mission was to introduce what we learnt from the book in our project.
 
Ow boy.. was it a wild ride.

We knew the code base was a mess, so the first thing to do was to clean it up step by step. Each PR was painful with a constant flow of questions of why we change things that are "working fine" (for now..).
It took a lot of time, but the result was clear - release cycle decreased significantly - noone prised us but at least we knew we did a good job.

During the course of events we developed own style - looking back it was not perfect but good enough. Having consistency in code style through the project was crucial later on.
Two of our regulars did quit the job, after that our team leader. Situation was looking pretty bad..
To be honest i panicked a bit and applied to a different company. Teammate (still junior at the time) decided to stay. Not so long after i've learnt that he was promoted to the regular and got two juniors more under his wings.
Two months after the transition to the new company i've met him while traveling to the new office so naturally we discussed a bit how things are going.

He was proud that thanks to the new code base he was able to introduce new members to the project very fast.

## IT Aiki - 合氣

When you are a junior developer that's pushing some ideas on "more experienced" team members you have to do it correctly or the efforts will be fuitile.
This can also happen in case of any authority level and might introduce a conflict which is a lot harder to resolve.

In my case code reviews proved themselves as great tool to share those ideas, simply because doing a code review requires one's attention.
On those foundations you can start the discussion about what you think is currently wrong and how you think it can be fixed with PR containing possible solution.
This helps to grow both you and your reviewer not only as a professional but also as a person.

I've also learnt something i call "IT Aiki" during this exercise which can be explained as "using someone's else expertize to empower own ideas".
This may sound a little manipulative and it is, but doing so for a good cause - cleaner and a more pleasant to work with code base - may be forgiven.
Fortunately most of the reviews we "juniors" had were "F2F" ones and thanks to that it was a lot easier to execute this technique.
When questions about "why are we doing it this way" popped out all we had to do was to point to some past event ( which might have not even happen ) where we decided it is a good practice to do it this way.
Ofcourse the reviewer was the person that proposed it back then because that's what the clean code promotes!

## Long story short

Most people are lazy by nature. Most of the time they know the correct way of solving a problem but will still take shortcuts in the end. Software industry is no different in this regard.
Things get a little bit more complicated when such a way of thinking sticks for too long - for example in a legacy project.
You, the person that just started working in it, you can make a difference.