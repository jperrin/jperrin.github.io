---
title: "Thoughts on CentOS Stream"
categories:
 - blog
---

I'm excited to see the CentOS project and Red Hat work together and collaborate around CentOS Stream, and I'd like to explain why I think this is a good move. I've been a member of the CentOS project for the last 16 years, and in that time I've had countless conversations with developers who were targeting enterprise deployments, but who wanted to push things just a little beyond what was currently available. In my early days with the project it was "I just need this new feature from PHP" or "I need this one option enabled in postfix". This was so common it spawned an entire cottage industry of 3rd party repositories like Elrepo, IUS, nux-desktop, and even our own CentOSPlus. Often these were features Red Hat would include in a future version of RHEL, but the timing and communication around these features was a mystery. Red Hat never announced release dates or upcoming features and for many developers, even for those internal to Red Hat this was a PROBLEM.

When I joined Red Hat to work on CentOS full time, they outlined the goal pretty clearly: "We want to showcase our upstream community work we intend to put in our layered products". Red Hat's developers were using CentOS to do their upstream development work, and our role was to help them. This quickly became a problem, because the way to get new work into RHEL was Fedora, but that's often not practical for a variety of reasons (Software Collections, modularity structure, release cadence, etc). Nothing here is new. Red Hat's Josh Boyer and Brendan Conoboy spoke at length about this challenge in their [Penrose Triangle](https://youtu.be/1JmgOkEznjw) talk at Flock in 2018

CentOS Stream represents several positive steps for Red Hat here.

 1. It makes RHEL development more transparent and reliable.
 2. It provides a way for ISVs and developers to contribute fixes and features.
 3. It provides a way for the community to provide feedback.

Did you download the RHEL8 public beta? Did you notice that the python setup looked VERY different between the GA and the beta? If you spent the 6 months between the RHEL beta and GA developing your app to work, it's possible you had the rug yanked out from under you. CentOS Stream solves that by providing constant updates so you can see what changes are coming, and adjust accordingly. Because RHEL's development is now transparent to the public, devs shouldn't be surprised by changes, they'll finally be able to see them coming.

Seeing what Red Hat is doing is one thing, but for those users I mentioned earlier who just needed that one new feature - they now have a way to collaborate with Red Hat to make it a reality. CentOS Stream provides a way for users to submit pull requests and to make their case for why it should be included. This obviously doesn't mean everyone will get their way, but it's a stark improvement from the past.

