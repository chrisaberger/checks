## Some Quotes to Sanity Checks Your Paper

I am fortunate to have recieved a lot of great advice from many great researchers throughout my PhD. As a result, now when I  write a paper (or just present research in general) I often find myself replaying many quotes from the people who taught me how to do research. For me, these quotes/advice serve as a sanity check to ensure that I am actually doing something that makes sense (which at times is much harder than it seems!). Further, when providing feedback on papers, these are the comments I most regularly give. In this post I have compiled the quotes that have stuck with me the most throughout my PhD. This is largerly for myself (so I remember my own sanity checks), but who knows maybe these quotes(/sanity checks) will resonate with someone else!

*Note that this post is focused on the presentation of experimental results. If you are interested in how to setup an experiment check out [this post](https://craberger.github.io/coffee/).*

The rest of this post is structured as the following: (1) the quote is provided, (2) the quote is explained, (3) an example of what not to do is provided, and (4) a fix showing what to do is provided.

1. [Show don't tell](#show)
2. [A Paper is Like an Onion](#onion)
3. [Reviewers Use AND Semantics](#and)
4. [Where is the ablation study?](#ablation)
5. [Lines better be crossing](#lines)
6. [A Paper is Not Like a Sitcom, There Should Be No Big Reveal at the End](#sitcom)
7. [You don't get credit for what you didn't do.](#credit)

<a name="show">
## "Show don't tell"

This is a simple one but it's suprising how often it is done wrong. The idea is simple: instead of telling someone how great your idea is or result is, let your experimental (or theoretical) results do the talking. Numbers speak louder than words.

### Problem
```markdown
In this paper we present System X and show that it performs well at 
task Y. 
```

The lack of precision is the problem with the writing above. It basically reads like 'We present System X and boy it feels good!' It is unclear what 'performs well' means and no baseline is specified. This can setup false expectations for a reader. What is 'performs well' means at least an order of magnitude to one person but your results show a 2x improvement. It is basically open to the interpretation of the reader to decide what this means to them. 

### Fix
```markdown
In this paper we present System X and show that it can outperform 
baseline Z by up to 10x at task Y while remaining within 10% of Z
at tasks A, B, and C. 
```

This statement is precise and not open to interpretation. Further, the reader knows exactly what to expect in the experiments section of the paper. Of course, we should know what 10x is with respect to but in the hopes of keeping this post generic.

<a name="onion">
## "A Paper is Like an Onion"

Alright now we are getting more out there! This quote refers to the structure of a paper, it should always be parallel in nature. In general the outline of your paper should unravel like the layers of an onion. One thing that is useful for this is setting up your introduction in (roughly) a structure that mirrors the rest of your paper. An easy place to do this is in the contributions. Let's take a look at an example outline.

### Problem
```markdown
1. Introduction (Contributions)
- We present an optimizer to automatically select among techniques.
- We show that two new techniques can lead to speedups in different 
scenarios.
- We present theory to show our new techniques are principled.
2. Background.
3. Theory
4. Techniques
5. Optimizer
6. Experiments
- End-to-end Comparison
- Micro Experiments Validating Optimizer
```

### Fix
```markdown
1. Introduction (Contributions)
- We derive a new bound showing that techniques A and B can lead to 
asympotic speedups.
- We present two new techniques, (1) A and (2) B, and an optimizer 
to optimally select between them. We show that A can lead to X 
speedups in scenario C. We show that B can lead to X speedups in 
scenario D.
- We evaluate System X and show that it can outperform baselines A, 
B, C on tasks D, E, and F. We show that our novel optimizer can 
provide up to X speedup on these various tasks.
2. Background.
3. Theory
4. Techniques
5. Optimizer
6. Experiments
- End-to-end Comparison
- Micro Experiments Validating Optimizer
```

<a name="and">
## "Reviewers Use AND Semantics"

This one is simple. The 1000 things you do right in a paper do not matter, but the one thing you get wrong does. The place this I most often screwed this up was when I tried to do too many things at the paper which sacrificied do a couple things really well.  A paper is like building a dam, you better make sure there aren't any holes.

### Problem
```markdown
We present technique X and show it is the best at tasks A, B, C, and D. 
```

### Fix
```markdown
We present technique X and show it under conditions Y and Z it can 
lead to a 30% improvement on task A while recovering 
state-of-the-art performance on task W. 
```

Of course there is no problem here if due dillegence has been done on validating tasks A, B, C, and D but you have to make sure that is true. Was every proper baseline considered? Was the experimental setting fully optimized? Did you tune all the parameters of your experiment properly? Was the previous literature/techniques setup and tested properly? This is a lot of work for 4 tasks! The underlying idea that it is better to do one thing well than many things just alright never changes. Go deep and fully understand one thing before jumping onto another.

<a name="ablation">
## "Where is the ablation study?"

The idea of an ablation study is simple yet effective: on important tasks break down and isolate the benefit every contribution you make in the paper. This idea is best explained through example:

### Problem
```markdown
Contributions:
-In this paper we present optimizations A, B, and C,
showing that they can lead to a 1000x performance 
advantage when compared to a design not implementing 
these techiniques.

Experiments Table:

        | Performance
        ______________
Task 1  |   10s
Task 2  |   20s
Task 3  |   30s
```

### Fix
```markdown
Contributions:
-In this paper we present optimizations A, B, and C, 
showing that they can lead to a 1000x performance advantage 
when compared to a design not implementing these techiniques.

Experiments Table:

        | Performance |  -A  |  -B   |  -C   
        _____________________________________
Task 1  |   10s       |  12s |  13s  |  14s
Task 2  |   20s       |  22s |  23s  |  24s
Task 3  |   30s       |  32s |  33s  |  34s
```

I got this one wrong a lot early on but the idea is simple: if you present some optimizations, you better validate their impact!  

<a name="lines">
## "Lines better be crossing"

This is probably the most important point for systems related papers. I am firm believer that given the rapidly evolving pace of software and hardware systems it is likely that no one is really going to care about how you built your system 10 years from now. What people will care about are the tradeoffs. Tradeoffs age well, systems hacks do not. When lines cross in a plot that indicates that there is a tradeoff. 

### Problem
<img src="images/bad.jpg" alt="hi" class="inline"/>

```markdown
Technique A always wins.
```

### Fix
<img src="images/good.jpg" alt="hi" class="inline"/>

```markdown
Technique A wins under conditions X while Technique B wins under 
conditions Y. We build a simple optimizer that automatically 
selects between these techniques based on the current condition.
```

Constant factor optimizations are not that interesting. Tomorrow there will be a new one. Tradeoffs are the interesting thing. There is no free lunch that is also an interesting lunch! (Ok maybe I am getting to excited by quotes that don't make sense at this point.)

<a name="sitcom">
## "A Paper is Not Like a Sitcom, There Should Be No Big Reveal at the End"

Many times I found myself wanting to write a paper like a narrative where I build up some exciting story before a mind blowing conclusion. This is wrong. The truth of the matter is that most people aren't patient and, as a general rule of thumb, I want to know if this section/paragraph/paper is worth reading in-depth as soon as possible. There is nothing wrong with this it is just human nature. So to combat this the best results should always come first. This is true in every section of the paper. In your abstract/introduction/contributions/experiments the best result should come first and should come often. It should be beaten over people's heads so that they cannot miss it. Let's take a look at two outlines for an experiments section, one that does not ensure this and one that does: 

### Problem
```markdown
Experiments:
-Micros (Ablation Study)
-Macros (End-to-End Comparison)
```

### Fix
```markdown
Experiments:
-Macros (End-to-End Comparison)
-Micros (Ablation Study)
```

The reason you want this structure is simple. As an outside reader I do not care about your micro-experiments I am unsure that this technique is useful when compared to the current state-of-the-art (this is what the macros validate!).

<a name="credit">
## "You don't get credit for what you didn't do."

I got burned by this one in my first paper. I thought I could just write my way around why I did not setup an experiment. Well, I learned that hard way that you cannot! If there is some experiment that can improve you paper drastically it should always be added in. Even if this experiment does not become a central contribution that appears in the paper, there is value in placing results in an appendix.

### Problem
```markdown
We test technique A under conditions X and Y. 
We omit a comparsion on technique Z because it
rarely occurs.
```

### Fix
```markdown
We test technique A under conditions X and Y. We present a comparsion 
on technique Z in the Appendix on conditions that we rarely 
encountered in practice.
```

This goes back to show don't tell! Better to withhold a paper that could be made better than hurry into a rushed submission.
