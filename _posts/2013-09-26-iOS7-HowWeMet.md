---
layout: post
title: "iOS7 and Me"
tags: 
- iOS7
- programming
- HowWeMet
- Apple
- interactive
- transitions
---
In the past few months I've been focused on Rails and other than that I've been hanging out with my wife and baby - who is walking now and it is insane! Like we have to have eyes on her at all times, it's been pretty intense and has limited my free time, but I digress.
 
This past weekend I thought it was about time I put some focus onto iOS. I signed up for the [Code School](www.codeschool.com) beta iOS7 course. It was a great course, but it was limited to the first half of the course that mostly covered appearance issues like the changes to UIFont with the additon of UIFontDescriptor, the addition In the past few months I've been focused on Rails and other than that I've been hanging out with my wife and baby - who is walking now and it is insane! Like we have to have eyes on her at all times, it's been pretty intense and has limited my freetime, but I digress.
 
This past weekend I thought it was about time I put some focus onto iOS. I signed up for the [Code School](www.codeschool.com) beta iOS7 course. It was a great course, but it was limited to the first half of the course that mostly covered appearance issues like the changes to UIFont with the addition of UIFontDescriptor, the addition of the status bar in your layout, and finally it went over custom transitions - which I'm probably going to go more in depth on later when I open source a navigation or two.
 
After going over the course I decided to dive into [HowWeMet](https://itunes.apple.com/app/howwemet/id657157238?mt=8) and start porting that over to iOS7. This also included a decision I made to change the navigation in the app from the sidebar style to tabbar. I also decided to [open source](github.com/wmtylerdavis/HowWeMet-iOS7) this code by ignoring one file in GitHub that has my Parse key information. Everything else is there for you to see.
 
I've cleaned up the code a lot. I got really sloppy with my pointer declaration. I was doing lots of NSArray* myArray, when I know the coding standard is NSArray *myArray. I also got sloppy on my properties by declaring some (nonatomic, retain) and others (strong, nonatomic). So in every file I touch I am fixing these cosmetic issues.
 
My current issue in the code is in my layout for the actual Meet story view. I had been doing everything in the loadView method and it worked well with a call to layoutSubviews. Now I'm conforming the code to iOS7 by doing my layout in viewWillLayoutSubviews (I'm still doing some stuff in loadView). My plan for tonight is to get in there some more and fix the bugs. I see lots of /* commenting out layout code */ in my future.
 
If you're interested in watching the process make sure to watch or start the [repo](github.com/wmtylerdavis/HowWeMet-iOS7).