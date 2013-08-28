---
layout: post
title: More objects, ViewController bloat, Testing, and Refactoring
tags: coding, iOS, build, phase, thoughtbot, bloat
---

I was listening to [Build Phase](https://learn.thoughtbot.com/buildphase/3) this morning, and they definitely brought up one of my greatest weaknesses which is not creating enough objects. This doesn't necessarily mean that my code isn't DRY, but instead it means there is usually a lot of bloat in my viewcontrollers. I couldn't help but compare this in my mind to my Rails experience so far, which led me to thinking about why I tend to let this happen in iOS but not so much in Rails.
 
First thing is that iOS development is a little bit slow. It takes a long time to get something meaningful to the screen, where in Rails it can take minutes. So once I've got something on the screen, I'm not as much in the mood to test and refactor it.
 
Second problem that I have is I'm not a good tester. I love RSpec in Rails, but I haven't found anything in iOS that is that intuitive. My test files can suffer from a similar bloat as the viewcontrollers. This is no bueno.
 
So obviously the simple solution, or at least the one the Build Phase guys suggest is to begin your project thinking about these things first. Design your classes meticulously for optimal code reuse and simplification. This all sounds nice, but unless you know exactly what the app will look like and the framework it is working with then these things are hard to do. From my experience the server-side has often been developed alongside iOS. So I'm not always able to predict what's coming along. 
 
### My plan ### 
I'm going to treat iOS as similar to Rails as possible. I'm going to write test driven code. I'm going to test. When a view controller gets hairy, I'm going to refactor the SOB. I don't care if it takes a day or two away from shipping product (see that's the key here - understanding that writing clean code is just as important as shipping product). Once the code is refactored I can then test. I have to remind myself that Git is my friend. As long as I'm branching and merging clean code I'm good. I don't have to worry about effing things up when I refactor. 