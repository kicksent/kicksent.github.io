# How to Debug:

I have been listening to an audiobook [The Complete Software Developers Career Guide](https://amzn.to/3c8aAzi) on my way to work. I highly recommend this book to developers that have long commutes or do daily low intensity cardio and want something valuable to listen to. This book has already reshaped many of my preconceived notions about several aspects of development and I'm only about half way through it.

## Backstory:

In April, I began my first job working on a software development team. The project is a few years old, so there is a large codebase that I have to learn and I am working bugs to learn what others have been doing, how the project has been designed, and to sharpen my debugging skills. Debugging is a skill that will serve me for the rest of my career if I can master it. It's inevitable that all developers will create bugs and having a strategy going in saves time. 

## The problem:

When I began debugging the project, I would find some value that was incorrect or missing, start up the debugger, and begin searching for the cause. **I had been told on a podcast that using a debugger well is the key to debugging!** The amount of time varied from a few minutes to a couple of days. When the debugging sessions were long, it became easy to forget what I had tried, which classes I had looked at, and even what the original bug was. Sometimes I ended up finding other bugs along the way, and fixed those, only to realize that I had not made much progress on the original issue. This process becomes mind numbing and I often found that at the end of the day my brain was just foggy and exhausted from the intense session of speculation and skepticism I had just put myself through.

## What does John Sonmez have to say about debugging? Use the debugger as a last resort.

_What?! How could this be true? I have learned that the debugger is a powerful tool, handed down from the gods of software engineering to break my code apart, and interrogate each variable for its secrets! Why would I not use this all powerful hammer the pound all of the bugs in my code flat into the ground?!_

Here are the steps he recommends:

1. Start by reproducing the bug. If I can't, I can get a tester to show me how the bug is produced. If I can't do this, I can't fix the problem, and I can't test it.

- Ok, this is obvious, but don't lose hope, keep reading.

2. Try to determine how I think the bug is happening, and think about ways that it could occur (without opening the debugger to check).

- John calls this the "Sit and Think" step. The idea here is to reduce the scope of the problem. If I can determine a few potential areas where the bug can occur, this will help me prevent the 10 hour debugging sessions where I inevitably look through every piece of code that component touches looking for abnormalities and causing short term confusion and brain fog.

3. Test hypothesis by writing a unit test(or another kind of test) .
  1. If a test fails on the case, then I can use that to test the problem. When it passes, I can be sure that it is resolved. (Remember that making a test fail is an important step in writing good tests.)
  2. If I write a test, and it passes, then I have a test that tests another piece of functionality.
  3. I now know, that the tests that are passing are not the issue, and can move forward knowing that I have tested those components and they work as intended. This narrows the scope of the problem and helps to break the problem down further as I progress.
     John uses the analogy of "closing and locking doors" as I traverse the problem.
  4. All of the above scenarios improve the code, and makes it more maintainable. Developers working on this code can now run the tests and check that they didn't break anything.

## Why is this approach better?

Instead of just fixing the current problem, I have eliminated the source of the problem. I also made the code easier to maintain with unit tests.


_These are just my own notes, John has much to say about debugging and code maintainability. Check out the audiobook [The Complete Software Developers Career Guide](https://amzn.to/3c8aAzi) Chapter 32 (Chapter 38 if using audible app). John is the founder of [simpleprogammer.com](http://simpleprogrammer.com) and is a pluralsite author sharing tons of valuable programming content online._