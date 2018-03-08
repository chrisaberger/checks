## Quotes to Sanity Checks Your Paper

I am fortunate to have recieved a lot of great advice from many great researchers throughout my PhD. As a result, now when I  write a paper (or just present research in general) I often find myself replaying many quotes from the people who taught me how to do research. For me, these quotes/advice serve as a sanity check to ensure that I am actually doing something that makes sense (which at times is much harder than it seems!). Further, when providing advice on younger students papers, these are the comments I most regularly provide. In this post I have compiled the quotes that have stuck with me the most throughout my PhD. This is largerly for myself (so I remember my own sanity checks), but who knows maybe these quotes(/sanity checks) will resonate will someone else!

*Not this post is focused on the presentation of experimental results. If you are interested in how to setup an experiment check out [this post](https://craberger.github.io/coffee/).*

The rest of this post is structured as the following: (1) the quote is provided, (2) the quote is explained, (3) an example of what not to do is provided, and (4) a fix showing what to do is provided.

## 'Show don't tell'

This is a simple one but it's suprising how often it is done wrong. The idea is simple: instead of telling someone how great your idea is or result is, let your experimental (or theoretical) results do the talking. Numbers speak louder than words.

### Problem
```markdown
In this paper we present System X and show that it performs well at task Y. 
```

The lack of precision is the problem with the writing above. It basically reads like 'We present System X and boy it feels good!' It is unclear what 'performs well' means and no baseline is specified. This can setup false expectations for a reader. What is 'performs well' means at least an order of magnitude to one person but your results show a 2x improvement. It is basically open to the interpretation of the reader to decide what this means to them. 

### Fix
```markdown
In this paper we present System X and show that it can outperform baseline Z by up to 10x at task Y while remaining within 10% of Z at tasks A, B, and C. 
```

This statement is precise and not open to interpretation. Further, the reader knows exactly what to expect in the experiments section of the paper. Of course, we should know what 10x is with respect to but in the hopes of keeping this post generic.

### "A Paper is Like an Onion"

### "A Paper is Not Like A Wedding, You Don't Wait to Show Off the Bride"

### "Reviewers Use AND Semantics"

### "Lines better be crossing"

### "You don't get credit for what you didn't do."

### "Where is the ablation study?"

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```


