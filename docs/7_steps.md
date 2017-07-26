# 7 Steps to Solve Algorithm Problems

Today, I viewed the video "7 Steps to Solve Algorithm Problems" by Gayle Laakmann McDowell - the author of [Cracking the Coding Interview](https://www.amazon.com/gp/product/0984782850/ref=as_li_tl?ie=UTF8&tag=hrctci-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=0984782850&linkId=4b0bb75d87b94d4378dd3bd245a7284b) book. In this video, Gayle describe her method for solve algorithms problems which consists 7 steps: listen carefully, example, brute force, optimize, walk through your algorithms, code and test. In this article, I will summary these steps base on what I learned from this video.

## Step 1: Listen carefully

> Every single detail in a question is necessary to solve it.

The first step is to listen carefully to the problem. So, generally speaking every single detail in a question is necessary to solve that problem - either to solve it all or to solve it optimally. So if there's some detail you haven't used in the question in your algorithm so far think about how you can put that to use because it might be necessary to solve the problem optimally.

Let me give you an example.

```text
You have two arrays, sorted and distinct
How did you find the number of elements in common between the two arrays?
```

A lot of people solve this problem and they'll get kind of stuck for awhile and what they'll do is they'll be solving the problem and they'll know the arrays are sorted but they haven't actually used the fact that it's sorted.

This *sorting* detail - it's not necessary just to find an algorithm but it is necessary to solve the problem optimally.

So remember every single detail in the problem and make sure you use it.

## Step 2: Example

> Make example big, no special cases

The second piece is to come up with a good example, so the last problem that I gave two arrays *sorted* and *distinct* compute the number of elements in common, most people's examples look like this.

```
# too small and special case
A: 1, 5, 15, 20
B: 2, 5, 13, 30
```

Yes technically if it's a problem but it's not very useful.

As soon as you glance at this example you notice that there's only one element common and you know exactly what it is and it's obvious because this example is so small and it's actually kind of a special case.

A better example is something like this

```
# larger and avoid special cases
A: 1, 5, 15, 20, 30, 37
B: 2, 5, 13, 30, 32, 35, 37, 42
```

It's much larger and you've avoided some special cases. One of the easiest ways of improving your performance on algorithm questions is just make your examples *larger* and really *avoid special cases*.

## Step 3: Brute force

> Better to have a brute force than nothing at all

The third step is to come up with a brute force algorithm. Now I'm not saying you need to go out of your way to come up with something slow, I'm really just saying, hey if the first thing you have is only something really really slow and terrible that's okay. It is so much better to start off with something slow then to start off with nothing at all. So it's fine if your first algorithm is slow and terrible whatever. However, and this is very very very important, I'm not saying to code the brute force. I'm saying just state your brute force algorithm, state its runtime, and then immediately go to optimizing.

A good chunk of the time on algorithm interview question will often be spent on optimizations. So that's step 4 and spend some good time on it.

## Step 4: Optimize

The fourth step is optimize and spend some good time on it.

## Step 5: Walk through your algorithms

> Know exactly what you're going to do before coding

* what variables & data structures?
* how, why, why do they change?
* what is the structure of your code

Then once you have an optimal algorithm or you're ready to start coding take a step back and just make sure you *know exactly* what you're going to do in your code.

So many people code prematurely when they aren't really really comfortable with what they're about to do and it ends in disaster. An eighty percent understanding of what you're about to write is really not enough for a whiteboard especially. So take a moment and walk through your algorithm and make sure you know exactly what you're about to do.

## Step 6: Code

> Use space wisely, coding style matters, modularize

Step 6 is to start coding and I'm gonna go into this in a bit of detail. So a couple things to keep in mind particularly when you're coding on a whiteboard. The first couple tips are kind of whiteboard specific but try to write your lines straight. I'm not gonna be judging you on your handwriting and things like that but when people start writing their lines and sharp angles they start to lose track over whether this if statement under this for loop or not. The second thing is use your board space wisely. If you don't need stuff up on the board anymore just erase it. Try to write in this top left corner etc.

Basically give yourself as much space as you possibly can to write your code. If you do run out of space though, it's ok to use arrows, that's fine, I'm really not gonna be judging you on this kind of stuff. So more important things.

**Coding style matters** (*consistent braces*, *consistent variable naming*, *consistence spaces*, *descriptive variables*)

Coding style matters even on a whiteboard but on a computer as well, so that means things like braces, naming conventions, or using camel case or underscores, things like that. Those kind of style things absolutely matter. I'm not that concerned over which style you pick, I don't care if you write braces on the same line or the next line but I do care a lot that you have a style and you stick to it. So be consistent in your style. When it comes to variable names, yeah I know it's an annoying to write long variable names on a whiteboard but descriptive variable names are important to good style. So one compromise here is write the good descriptive variable name first and then just ask your interviewer, hey is it okay if I abbreviate this the next time. So that'll be a nice little compromise - you'd show that you care about good variable names but you also don't waste a lot of time.

**Modularize** (*before. not after*)

Last thing I want to talk about is modularization. Modularize your code up front and just any little conceptual chunks of code, push that off to another function. So suppose you have three steps in your algorithm - process the first string, process the second string,  and then compare the results. Don't start writing these for loops that walk through each string in the very beginning. Instead write this overall function that wraps these three steps. So step one, step two, step three, and then start drilling in and going into all the details there. Remember any conceptual chunks of code push those off to other functions, don't write them in line. 

## Step 7: Test

> Analyse: think about each line, double check things that look weired/risky (for-loop that decrement, math) 

> Use test cases (smaller test-cases first (faster to run, you will problably be more through, edge cases, big test cases)

Then once you're done with the coding you have to start testing your code. One of the mistakes a lot of people do here is they take their big example from step 2 and throw that in as a test case. The problem with that is it's very large so it will take you a long time to run through but also you just used that to develop your code, so if here's an oversight there, the problem will probably repeat itself here. 

What's a better step to do, what's a better process to do, is just walk through your code line by line and just think about each line up front not with the test case but just consider, is it really doing the right thing?

Double check anything that looks weird, so for loops that decrement instead of increment and any math at all is a really common place for errors. Just think, look at your code analytically and think what are the most likely places for errors to be and double-check those.

**Start with small rather than big**

Then once you start with actual test cases start with small test cases rather than big ones. Small test cases work pretty much as effectively as big test cases but they are so much faster to run through, and in fact because they're faster people tend to be much more thorough so you're much more likely to actually find bugs with small test cases than big test cases. So start with small test cases then go in to edge cases after that and then if you have time maybe throw in some big test cases. A couple last techniques with testing. The first one is make sure that when you're testing you're really thinking about what you're doing. A lot of people when they're testing they're just walking through their code almost like they're a bot, and they only look to see if things made sense at the very end when they look at their output. It's much better to really think as you're testing, this way you find the bug as soon as it happens rather than six lines later at the very bottom.

**Test your code not your algorithm**

The second thing is when you're testing make sure that you're actually testing your code and not your algorithm. An amazing number of people will just take their example and like just walk through it again as though they're just walking through their algorithm but they're never even looking at their code, they're not looking at the exact calculations their code actually did. So make sure that you're really testing your code.

**Find bugs**

Then the last thing is when you find in a bug, don't panic. Just really think about what caused the bug. A lot of times people will panic and just try to make the first fix that fixes it for that output but they haven't really given it some thought and then they're in a much worse position because if you make the wrong fix to your code, the thing that just fixed the output but didn't fix a real bug you've not fixed the actual bug, you've made your code more complex, and you potentially introduced a brand new bug and you're in a much worse position. It's much better to just when you find the bug, it's ok, it's not that big of a deal to have a bug it's very normal just really think through what the actual bug, where the actual plug came from.

**Remember**

* think as you test (don't be a bot)
* test your code, not your algorithm
* think before you fix bugs. Don't panic! (wrong fixes are worse than no fix)

## Suggested Reading

* [7 Steps to Solve Algorithm Problems. Gayle Laakmann McDowell](https://www.youtube.com/watch?v=GKgAVjJxh9w&list=PLM0_NsFSjrgC72cExkBI4Iz99SBTzYG-u&index=4)

