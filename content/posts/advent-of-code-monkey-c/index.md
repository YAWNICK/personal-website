---
title: "Advent of Code 2022 on my Garmin Watch"
date: 2022-12-22T21:30:30+01:00
draft: false
disable_share: true
categories: ["Programming"]
---

**[Advent of Code](https://adventofcode.com/)** is a yearly programming advent calendar with puzzles being released from the 1st to the 25th of December. The puzzles usually follow some christmassy storyline and substantially increase in difficulty throughout the month. I've completed AoC in 2020 and 2021 and sometimes found it scary how much this challenge consumed me, but it was always worth it for the joy of finding the solutions and learning new things. 

This year I've had the idea to try to solve some AoC puzzles on my Garmin Forerunner 235 running watch. I once did a university project using my FR235 ([an app](https://github.com/YAWNICK/CatchCounter) that counted juggling catches using the accelerometer data from the watch) and from that experience I thought solving an AoC problem on the watch might just be possible. 

## The Setup

Most (if not all) Garmin watches and other devices nowadays come with ConnectIQ which is a platform for apps, widgets, data fields, etc. for different devices. Apps can be developed using Garmin's own programming language called Monkey C. When the watch is connected to a phone via Bluetooth the phone (with the Garmin Connect App) can act as a proxy to the web, which enables the watch app to make http requests. That's how I download the input. No messing around with the input in an editor first:) 

Not so long ago Garmin made development infinitely easier by releasing a VS Code extension, which was helpful for my AoC adventures with Monkey C. The app can be tested and debugged with the simulator (which is way faster than my actual physical watch), so I could conveniently only upload the correct code to my watch.

![>Image of my setup<](images/dev-setup.jpg)
(Can you guess which day the notes are for?)


---

## Solving AoC Puzzles

Here's the **[GitHub Repo](https://github.com/YAWNICK/MonkeyAOC)**.

And here's my **[Upping the ante submission](https://www.reddit.com/r/adventofcode/comments/z9he28/comment/iz92hv9/?utm_source=share&utm_medium=web2x&context=3)** on the AoC Subreddit (includes links to videos).

I've built the app (and framework if you will) in November to be able to start AoC only having to worry about the actual puzzle. I also always solved the puzzle in Python first to know what my correct solution was.

#### The `WatchDogTrippedError`

This was the first big problem. If some function of an app runs for too long (i.e. doesn't give up the cpu) the app crashes with an error. While this is probably important because other parts of the watch need the cpu as well, it makes long calculations for AoC problems more difficult. My solutions all had one big main loop and every day I needed to figure out how many runs of the main loop I could do before I had to voluntarily yield. The voluntary yield was basically a 50ms timer with a callback method which reported the progress and then jumped back into the solver. Reporting the progress and printing it out on the screen was handy, because my solutions take around 1-2 minutes on my watch to complete. Since all the variables local to the funtion with the main loop are lost after the yield I saved the state in class variables and designed the main loop so that it could continue just where it left off before the yield. The state usually included some `i` that iterated over the input and some intermediate result.

A typical Solver class:

{{< highlight javascript "linenos=table">}}
class Solver {

    // Boilerplate
    var app;
    var input;
    var timer;
    var part;
    var cent;
    var percent;

    // Day specific variables
    var i;
    var result;

    function initialize(app, input) {
        me.app = app;
        me.input = input;
        me.timer = new Timer.Timer();
    }

    function reportProgress() {
        me.app.onProgress(me.percent.format("%.2f"));
        // me.app.onProgress prints the progress and 
        // then calls solver.continueSolving()
    }

    function continueSolving() {
        iterate();
    }

    function solve(part) {
        me.i = 0;
        me.result = 0;
        me.part = part;
        me.cent = me.input.length();
        me.app.initiateProgress();
        me.iterate();
    }

    function iterate() {
        ...
        var finished = false;
        var wdcnt = 0;  // watchdog count
        while (wdcnt < 200) {
            ...
            // calculate
            ...
            if (finished) {
                me.app.onresult(me.result);
                return;
            }
            wdcnt += 1;
        } 
        me.percent = me.i.toFloat() / me.cent * 100;
        me.timer.start(method(:reportProgress), 50, false);
    }
}
{{< / highlight >}}


On one day I was down to 10 iterations before having to yield, so it's pretty safe that for some later problem I would need to split up the calculations even more (however I never got so far to actually run into this problem).

#### Other Challenges

The other challenge were the limited language features and space. I've solved the previous 2 years in Python, so this was quite the change. The input always comes in as a string. But in Monkey C, strings can't be indexed. On usual AoC inputs, however, converting the input string to a char array would cause me to run out of memory. What's possible though is to get substrings and find the first occurrence of a string in a string. So to consume a line of the input I would grab a substring starting at `i` that is long enough to contain the next `\n`, then find the `\n` and substring again to finally get the line. 

Maybe in future problems I would have liked to use other features of the watch OS (like persistent storage), but I wanted to make it work for my Forerunner 235 which only runs on Connect IQ version 1.4, which at this point is quite old...

To be honest I didn't run into too much other space problems, but that's because I only made it to day 7 (as of 2022). 

## How far can the watch go?

After finishing day 1 I felt half satisfied. After day 3 I thought that I could get used to this and maybe the first 5 days are doable (I remembered from the last years that day 6 usually was the first where it starts to get tricky). After finishing day 7 I was ready to call this challenge a success, but at the same time I had gotten the hang of it and I got scared because maybe all 25 days are doable (maybe not always with my own algorithms, but maybe with some help from the Reddit Megathreads). But this was also the busiest I've ever bin in december outside of Advent of Code and I do want to finish it at all which started to take more time around day 16, so I think this is fine. 

Also, the longest run I've done with the watch is 22km, so I say it stands 1:0 (or 22:7?) for *running* against *AoC* in the category of "Best things to do with a Garmin Forerunner 235".

## But ... why?

1. I learned new things.
2. AoC is fun!
3. Maybe this codebase can be a helpful resource for others learning Monkey C or a reference for myself for future Monkey C projects.

Happy Holidays.