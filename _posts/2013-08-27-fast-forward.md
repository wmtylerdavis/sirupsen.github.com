---
layout: post
title: "How to Fast Forward"
tags:
- github
- git
- fast forward
- repo
---
 
## or why I fork shit I never contribute to
 
I've noticed a trend that I am definitely a member of - lots of people fork repositories only to never contribute a single line of code, let alone contribute and submit a pull request. In my work with HowMuch I did actually end up forking and contributing code to a couple of [projects](github.com/HowMuchTo). These were usually just single line or only a few line fixes to either add a feature as I did with KGModalView - which there was definitely a more elegant solution for (which is why my pull request was denied) or to fix a bug - which isn't really a bug but we didn't like the way that the countdown in JDFlipNumberView was flipping - in our minds it was upside down.
 
When using [CocoaPods](cocoapods.org) you can easily point the pod in your podfile to your forked repo like so:
 
    pod 'JDFlipNumberView', :git => 'https://github.com/HowMuchTo/JDFlipNumberView'

For the most part I do nothing with my forks. So why fork? Well when you're new to programming it is extremely hard to find open source projects to contribute to. So my feelings on this are only contribute to projects you use. Now it would be lovely to be able to dive into AFNetworking and really understand what is all going on, but that's a big fish to fry. My rule is just to fork everything I use and some projects I plan to use. If I find a bug or need an enhancement while using the project, then that grants me an incredible opportunity to contribute to open source. If I don't, then I don't and there was no harm done in forking the repo. Before you add any code to your forked repo, you are going to want to verify it hasn't already been done or there weren't additional changes that you need to take in effect. To do this you need to fast forward to the current version. Here is the down and dirty on fast forwarding your forked repository:
 
    fork repo
    time goes by
    git remote add upstream https://github.com<forked repo>
    git merge upstream/master
