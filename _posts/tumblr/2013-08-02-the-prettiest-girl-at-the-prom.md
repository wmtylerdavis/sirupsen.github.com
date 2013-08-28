---
layout: post
title: The prettiest girl at the prom
tags: 
---
I feel like I’m in a good position right now. I’ve got several companies interested in me, so of course it feels like all I’m doing right now is interviewing. It feels great to be in this sort of position in August. December seems like a long but short time away.

I’m still working on Rails. I want to be as diverse as possible. Ultimately I will build an iOS counterpart to the Rails app I’m currently working on. I feel like this will round out my experience a bit. When that happens I will probably start applying to Rails positions as well.

The interviews haven’t thrown me too much so far. Overall great interviewers that were easy to understand. I’ve had some OO design questions and lots of iOS/Objective-C specific questions. Amazing that even after all this time I’m still no good at explaining ARC.

The data structure questions haven’t been as intense as I thought they would be. I was asked to reverse a linked list. Also asked to parse a file with rules that for every ‘{’ you needed a ‘}’ and for every ‘(’ you needed a ‘)’. I first stated that I may use a HashTable and just verify that each had the right corresponding number. I was then told that something like this ” { ( } )” would be invalid. So the next approach I took was these two small classes:

{% highlight java %}

    public class WrongBracketException extends Exception {
        public WrongBracketException(String message) {
          super(message);
        }
    }
    class bufferedFileReader ( char[] a) {
    
      Stack<Character> stackOfBrackets = new Stack<Character>();

      for(int i = 0; i < a.length; ++i) {
        switch (a[i]) {

          case ‘}’:
            if (stackOfBrackets.peek() == ‘{‘)
              stackOfBrackets.pop();
            else throw new WrongBracketException(“Should match {“);
            break;

            case ‘)’:
              if (stackOfBrackets.peek() == ‘(‘)
                stackOfBrackets.pop();
              else throw new WrongBracketException(“Should match (“);
              break;
            case ‘{‘:
            case ‘(‘:
              stackOfBrackets.push(a[i]);
              break;
            default:
              break;
        } // end switch
      } // end for loop
    } // end class bufferedFileReader
    {% endhighlight %}
