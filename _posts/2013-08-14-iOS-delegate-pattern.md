---
layout: post
title: iOS Delegate Pattern
tags:
- coding
- iOS
- delegate
- pattern
- remote
- programming
---

In the course of iOS job interviews there always tends to be a question about the iOS delegate pattern, their concerns (cycles) and maybe they will even throw in some random question about a block in relation. 

1. What is a delegate?

	Sometimes in iOS it is beneficial in a class not to execute code, but instead to ask a delegate to execute some code for you. A great example of this is done by the UIAlertView class. There is a lot of benefit to knowing when a button was pressed in the UIAlertView, but Apple developers have no clue what you'd be using the alert for so they create a protocol. 

2. Protocols in iOS:

	A protocol is a list of methods with no definitions. 

3.	Describe the “delegate” pattern in Objective-C.

	Class A (UIAlertView) creates a protocol and adds an instance of the protocol as a property. Class B (YourViewController) has to implement the protocol. When class A is created its delegate property is set to class B.  

4.	What are some of the memory concerns related to this pattern and how they can be avoided?

	An object cannot be deallocated until all of its strong references are released. A retain cycle can occur if two objects have strong references to each other, causing a memory leak. So here B creates A. B sets itself as A’s delegate. Then B is released by its owner If A had retained B, then B wouldn’t be released. Therefore delegates should use a weak reference. 

5.	Delegate vs Blocks???

	Delegate callbacks are more process oriented and blocks are more results oriented. If you just want the information you are requesting then use a block. Blocks are associated with asynchronous actions and single instance uses (if an object is a singleton, use a block).Delegates are correct when you need ongoing communication. If an object has more than one distinct event, use delegation.

Here is some sample code from the example above: 
	{% highlight objective-c %}
    
    @class ClassA;

	@protocol ClassADelegate <NSObject>

	-(void)someMethod:(ClassA*)classA;
	@end

	@interface ClassA : NSObject 
	{ }

	@property (nonatomic, assign) id<ClassADelegate> delegate;
	@end

 	@interface ClassB : NSObject <ClassADelegate> 
	{ }
	@end

	@implementation ClassB

	// where needed classA.delegate = self

	- (void)someMethod:(ClassA*)classA 
	{ 
 		// do something 
	}
	@end
	{% endhighlight %}
