---
permalink: /codereview/:title
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
Two of our regulars did quit the job, after that our team leader. Situation was looking pretty bad.
To be honest i panicked a bit and applied to a different company. Teammate (still junior at the time) decided to stay. Later on i've learnt that he was promoted to the regular and got two juniors more under his wings.
Two months after the transition to the new company i've met him while traveling to the new office so naturally we discussed a bit how things are going.

He was proud that thanks to the new code base he was able to introduce new members to the project very fast.

## IT Aiki - 合氣

When you are a junior developer that's pushing some ideas on "more experienced" team members you have to do it correctly or the efforts will be fuitile.
This can also happen in case of any authority level and might introduce a conflict which is a lot harder to resolve.

Code reviews are a great way to share those ideas, simply because doing a code review requires one's attention.
On those foundations you can start the discussion about what you think is currently wrong and how you think it can be fixed with PR containing possible solution.
This helps to grow both you and your reviewer not only as a professional but also as a person, but ofcourse there are few things worth keeping an eye on:

- **It is very easy to hurt someone with harsh comments even if to you they look harmless**

    We are an emotional creatures. We are also built in a way that needs something more than words alone to understand the message.
    Comments do not contain tone, gestures, none of the body language our brain can analize. That's why they should be clear, polite and written with non-invasive words.
    This also depends on how well review participants know each other.
    
    
    
- **