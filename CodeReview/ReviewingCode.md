# A Guide to Scientific Code Review
*Compiled from multiple sources, each is linked below*

*Created by Hannah Holland-Moritz*  
*Date: March, 23rd, 2022*

## Background
The purpose of code review is to improve coding practices, and to help catch bugs that might otherwise be missed.

The goals of code review are to share knowledge, improve code quality, make science more repeatable.

## How to get the most out of a code review [for authors]
Adapted from [Ariel Rokem's excellent guide](https://uwescience.github.io/neuroinformatics/2017/10/08/code-review.html)

* Similarly to what you'd do with a paper you'd like reviewed, if you want your code reviewed for a specific purpose, make sure to point out where you'd like to focus. The focus could be one of the "big picture" review categories below (e.g. take a look at my statistics) or it could be flagging specific sections of the code you want reviewed (e.g. "Please take a look at lines 104-300")
* Give reviewers necessary context. This potentially includes an explanation of your data (and how it was generated), the goal of your code, and maybe how you expect your code to be used by you or by others. Don't forget to provide the reviewers with everything they need to run the code, this is often referred to as a "minimal working example" in coding forums.
* Let your reviewer know your timeline, and give them the code with sufficient time for them to do a thorough review. Research has shown that effective code reviews are between 200-400 lines of code at a time and that no more than 500 lines should be reviewed in an hour. Take these constraints into account and plan accordingly when requesting a review. If necessary, highlight 200-400 lines of code that need detailed focus to fasttrack review.
* Approach code review with a growth mindset. We are all trying to improve our abilities as coders and here to learn from each other.
* It's okay to request review of code that doesn't work yet. Just make sure that this is clear in your review request, and highlight areas you'd like the reviewer to focus on so that if you want them to help troubleshoot the parts that don't work, they can, or if you're looking for feedback on code that already works, they don't spend time on the parts that don't work.


## How to review code [for reviewers]
Adapted from [Ariel Rokem's excellent guide](https://uwescience.github.io/neuroinformatics/2017/10/08/code-review.html)

1. **Read the code through first.** Get a general sense of the intended purpose. Just like if you were reviewing a paper, write a couple of sentences of what you think the author intended to do, and your general impression.
2. **Ask questions.** Ideally you know what the author hopes to gain from the review before you start the review, but also ask questions. Make sure you understand the author's intentions and what they want feedback on.
3. **Read the details with a focus on modularity and design.** Modularity refers the the ability of pieces of code to be substituted out or in of a pipeline. [Wikipedia definition](https://en.wikipedia.org/wiki/Modular_programming): _"Modular programming is a software design technique that emphasizes separating the functionality of a program into independent, interchangeable modules, such that each contains everything necessary to execute only one aspect of the desired functionality."_ Code that is modular is more flexible because it can handle different inputs or be moved from one use to another. It's easy as an author to focus on the details of the code and reviewers can help by providing a big-picture view to the authors. This might mean making the code more modular or thinking about ways it might be used that go beyond the author's original intentions.
4. **Read the details with a focus on the math/statistics.** Scientific code often implements mathematical and/or statistical ideas. If it is called for, make sure that you understand the mathematical ideas that are implemented and the ways in which the math got transferred to code. This can be one of the hardest things to do in review, and a common source of error in writing code.
5. **Read the details with a focus on performance.** For this read-through think about the performance of the code and focus on areas that look like they might be performance bottle-necks. The author may have pointed these areas out in their review request, or you might identify them as you look at the code. Do you have suggestions that could improve performance at these bottlenecks? For example, many software languages used in scientific computing provide substantial advantages for vectorization of mathematical operations that are repeated over large arrays ([R does this!!](https://swcarpentry.github.io/r-novice-gapminder/09-vectorization/), [and has other ways to improve performance](https://www.r-bloggers.com/2016/01/strategies-to-speedup-r-code/)). Potentially there are libraries or ways to reimplement the algorithm that might be more efficient (you don't have to solve the problem for the author, but if a suggestion comes to mind, offer it.). Since learning how to use new functions and libraries can sometimes be cumbersome, consider the costs and benefits of adopting a new tool when offering advice about how to improve performance.
6. **Read the details with a focus on formatting, typos, comments, documentation and overall code clarity.** After larger concerns have been addressed, it's time to focus on the style. Give feedback about choice of variable names, typos in documentation, and comments. Make sure to also read the documentation and make sure it's clear and understandable to an outsider. Sometimes you'll already have addressed some of these issues in the big-picture overview, but here is where you catch everything else. Although this is an important aspect of code, the number of comments you can leave in this part of the review can be large, so consider using a "nit" prefix to indicate that they are a bit nit-picky ex: `nit: misspelled "displaced"`. This allows authors to address them without stressing about them.
7. **Read a final time, focus on the good.** Comment on what worked, was clever, or what you liked about the code and comments. This not only helps the author realize where they're doing well, but also helps you as a reviewer improve your skills as you will be forced to reflect on what worked as well as what did not.

### Areas to focus on in a code review for the reviewer:
1. Functionality - does the code do what the author intended?
2. Complexity - can another person easily understand the code?
3. Naming - are variables, functions, etc. well-named? (i.e. descriptive)
4. Comments - are there clear and useful comments throughout the code
5. Documentation - is there good documentation about what the code does and how to use it?

### How to improve code review discussions
1. Give feedback about the code not the author
2. Explain your reasoning
3. Remember their may be multiple correct solutions to a problem
4. Approach discussions with growth mindset (both reviewer and reviewee)
5. Coders are humans with feelings
6. Use the compliment sandwich method of feedback.

```
Something they did well
------------------------------
Something that could be changed
------------------------------
Something else they did well
```
### Other considerations for a reviewer
* Only review code that is 200-400 lines long. [Research](https://smartbear.com/learn/code-review/best-practices-for-peer-code-review/) shows that reviewers can’t effectively review more than that in one sitting. The same research suggests that you should expect to spend about 60 minutes reviewing 500 lines of code, and that you should take your time doing it. This means that you should take a break after about an hour of reviewing code.

* Code is a creative effort by a human being who has put a lot of time and energy into creating it. Even if you think they have made a mistake in their code or methodology, keep an open mind and express your opinion in a way that is respectful and constructive.


## An example rubric for code review
Adapted from [the Access Code course rubric](https://github.com/accesscode-2-1/user-manual/blob/master/code-review-rubric.md). Has been modified to reflect Ariel Rokem's guide above.

| Criterion | Excellent | Good | Adequate | Developing |
|---|---|---|---|---|
| **Program Specifications / Correctness** | No errors, program always works correctly and as the author intended. | Minor details of the author's intentions are violated, program functions incorrectly for some inputs. | Significant details of the authors intentions are violated, program often exhibits incorrect behavior. | Program only functions correctly in very limited cases or not at all. |
| **Modularity and Design** | Code is well-structured and modular, it would be easy to adapt the code to other situations and the flow is logical and easy to follow. | There are some areas where code could be made more module (i.e. repeated sections could be reduced to functions), some areas lack structure. | There is poor organization in large sections of the code, or large sections that not modular due to disorganization in code structure.  | The design of the code is very disorganized and not linear. |
| **Mathematics and Statistics** | All mathematical and statistical operations are performed correctly and are appropriate to the goal of the code. | There are some mathematical or statistical errors, or places where different approaches may be more appropriate. | There are many mathematical or statistical errors. Many operations used are not aligned with the goals of the analysis. | The mathematics and statistics used are not appropriate or aligned with the goals of the analysis. |
| **Code Efficiency and Performance** | No errors, code uses the efficient approach in every case. | N/A | Code uses poorly-chosen approaches in at least one place. | Many things in the code could have been accomplished in an easier, faster, or otherwise better fashion. |
| **Readability** | No errors, code is clean, understandable, and well-organized. | Minor issues with consistent indentation, use of whitespace, variable naming, or general organization. | At least one major issue with indentation, whitespace, variable names, or organization. | Major problems with at three or four of the readability subcategories. |
| **Documentation** | No errors, code is well-commented. | One or two places that could benefit from comments are missing them. | File header missing, complicated lines or sections of code uncommented or lacking meaningful comments. | No file header or comments present. |

### Program Specifications / Correctness

This is the most important criterion. A program must meet its specifications (i.e. do what the author or author's supervisor intended it to do) and function correctly. This means that it behaves as desired, producing the correct output, for a variety of inputs.

### Readability
Code needs to be readable to both you and a knowledgeable third party. This involves:

* Using indentation consistently (e.g., every method's body is indented to the same level)
* Adding whitespace (blank lines, spaces) where appropriate to help separate distinct parts of the code (e.g., space after commas in lists, blank lines between methods or between blocks of related lines within methods, etc.)
* Giving variables meaningful names. Variables named `A`, `B`, and `C` or `foo`, `bar`, and `baz` give the reader no information whatsoever about their purpose or what information they may hold. Names like `principal`, `maximum`, and `counter` are much more useful. Loop variables are a common exception to this idea, and loop variables named `i`, `j`, etc. are okay.
* The code should be well organized. Methods should be defined in one section of the program, code should be organized into methods so that blocks of code that need to be reused are contained within methods to enable that, and methods should have meaningful names.

Please refer to the [Hadley Wickam's R style guide](http://adv-r.had.co.nz/Style.html) for an idea of what 'Excellent' readability might look like.

### Code Efficiency
There are often many ways to write a program that meets a particular specification, and several of them are often poor choices. They may be poor choices because they take many more lines of code (and thus your effort and time) than needed, or they may take much more of the computer's time to execute than needed. For example, a certain section of code can be executed ten times by copying and pasting it ten times in a row or by putting it in a simple for loop. The latter is far superior and greatly preferred, not only because it makes it faster to both write the code and read it later, but because it makes it easier for you to change and maintain. A key thing to balance in code efficiency is readability. Sometimes code can become so "efficient" in terms of the number of lines it takes up that it becomes hard to read and/or interpret. On the flip side, code that has many duplicated sections that could be reduced to a loop may also be hard to read or interpret. Settling for a middle ground is best.

### Documentation

Every file containing code should start with a header comment. At the very least, this header should contain the name of the file, a description of what the included code does, and the name of its author (you). Other details you might include are the date it was written, a more detailed description of the approach used in the code if it is complex or may be misunderstood, or references to resources that you used to help you write it.

All code should also be well-commented. This requires striking a balance between commenting everything, which adds a great deal of unneeded noise to the code, and commenting nothing, in which case the reader of the code (or you, when you come back to it later) has no assistance in understanding the more complex or less obvious sections of code. In general, aim to put a comment on any line of code that you might not understand yourself if you came back to it in a month without having thought about it in the interim.

## Code Review Comment Prefixes
Adapted from [Christian Emmer's blog post](https://emmer.dev/blog/code-review-comment-prefixes/)

Consider using these prefixes to improve effciency of comments in code review:
* Props/praise (PP): if you want to thank someone or praise what they've done.
```
# PP: I love how you cited the paper that you got this method from in this comment
```
* Question (Q): Questions ask for clarification. They don't suggest a change but the answers might inform future directions of the code
```
# Q: Could you teach me what this code is doing?
# Q: Will this still work if you change xxx section as you plan to do above?
```
*  Nit/nitpick/opinion (nit): this is for unimportant comments (potentially opinions) that don't need to be addressed but would be nice if they were. Authors should be free to disregard nitpicks to focus on larger challenges in their code.
```
# nit: this variable name could be replaced with one that is more descriptive
# nit: your comment above contains a typo
```

* Suggestion/FYI (S/FYI): A less opinionated comment that offers an alternative solution or points out information that might be unknown to the author
```
# FYI: There is a function in the vegan package that already does this.
# S: Since you'll need to use this calculation elsewhere, consider moving it earlier in the code
```
* Convention (C): Pointing out that the code doesn't conform to standards, either organization/lab standards, or the standards that the author(s) have set for themselves,
```
# C: typically tidyverse pipes are indented starting with the second line.
# C: usually i and j are reserved for loop iterators, consider renaming this variable
# C: the spacing here doesn't comply with the R style guide, which you're trying to follow.
```
* Blocking (B): Blocking changes are changes that must be made (or the code is blocked from moving forward). These are errors in the fundamental calculations or methodology that prevent functionality of the code unless they are fixed. Often in scientific coding, but not always, these are errors in mathematics or statistics, however they can also be related to design, performance, or other software vulnerabilities
```
# B: a t-test is inappropriate here, use an anova (function aov()) when you have more than 2 categories
# B: Your comments indicate you mean to calculate the difference between the control and the treatment, but here you are comparing two treatments. 
```

## Other Resources
Google's code review guidelines: [https://google.github.io/eng-practices/review/]()

Tips for your first code review from Khan academy: [https://blog.khanacademy.org/tips-for-giving-your-first-code-reviews/]()
