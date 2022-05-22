# Week 6: Lab Report 4

Welcome to my fourth lab report! This lab will be going over code debugging.

Just some reminders: 
- My name is Nhan Quach
- My group leader is Elias
- My team members are as follows:


| Member 1 | Member 2 | Member 3 | Member 4 | Member 5 | Member 6 |
| -------- | -------- | -------- | -------- | -------- | -------- |
| Nhan     | Tyler    | Kayla    | Diego    | Jas      | Snehal   |

## Links to the Repositories for MarkdownParse

Mine: [ima_quack](https://github.com/ima-quack/markdown-parser)

Reviewed: [astoriama](https://github.com/astoriama/markdown-parser)

---

# Testing Snippets
For this Lab Report, I will be testing the MarkdownParse.java file with three new testing snippets.

**Snippet 1**
>     `[a link`](url.com)
>
>     [another link](`google.com)`
>     
>     [`cod[e`](google.com)
>
>     [`code]`](ucsd.edu)

The expected output from `getLinks` on **Snippet 1** should be ['google.com, google.com, ucsd.edu]. Based off of the CommonMark demo site.

![snippet1](images/snippet1.png)

**Snippet 2**
>     [a [nested link](a.com)](b.com)
>
>     [a nested parenthesized url](a.com(()))
>
>     [some escaped \[ brackets \]](example.com)

The expected output from `getLinks` on **Snippet 2** should be [a.com, a.com(()), example.com]. Based off of the CommonMark demo site.

![snippet2](images/snippet2.png)

**Snippet 3**
>     [this title text is really long and takes up more than 
>     one line
> 
>     and has some line breaks](
>          https://www.twitter.com
>     )
> 
>     [this title text is really long and takes up more than 
>     one line](
>     https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
>     )
> 
> 
>     [this link doesn't have a closing parenthesis](github.com
> 
>     And there's still some more text after that.
>
>     [this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/
>
>
> 
>     )
>
>     And then there's more text

The expected output from `getLinks` on **Snippet 3** should be [https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]. Based off of the CommonMark demo site.

![snippet3](images/snippet3.png)

# Implementation of Snippet Tests

## Personal Repository 

![test_implementation](images\test-setup-personal.png)

Within my personal implementation of MarkdownParseTest.java, I created some instance variables to populate the result and files of each of the tests. This was so that I can then create a `setUp` method which streamlines the actual test writing.

![test](images\test-personal.png)

### For Snippet 1

When running **Snippet 1** on my implementation of MarkdownParse.java, it fails with the following result:

![result1](images\result1.png)

### For Snippet 2

When running **Snippet 2** on my implementation of MarkdownParse.java, it fails with the following result:

![result2](images\result2.png)

### For Snippet 3

When running **Snippet 3** on my implementation of MarkdownParse.java, it fails with the following result:

![result3](images\result3.png)

## Reviewed Repository

![test_implementation_other](images\test-setup-other.png)

Within the MarkdownParseTest.java of the individual who I reviewed, I copied over the same structure as my test implementation. However, you can see the original methodology which the other individual used to create their tests from below.

![test_other](images\test-other.png)

### For Snippet 1

When running **Snippet 1** on the reviewed implementation of MarkdownParse.java, it fails with the following result:

![result1_other](images\result1_other.png)

### For Snippet 2

When running **Snippet 2** on the reviewed implementation of MarkdownParse.java, it fails with the following result:

![result2_other](images\result2_other.png)

### For Snippet 3

When running **Snippet 3** on the reviewed implementation of MarkdownParse.java, it fails with the following result:

![result3_other](images\result3_other.png)

# Diagnosis

## Snippet 1

The issue with **Snippet 1** was that the code block signaler \` was insinuating specific behavior for the way links should work. Thus, I believe within my `getLinks` method, I could make a change of implementing a "code block" search which sees if there is a competing Code Block line occuring before the Open Brackets. It may go something along the lines of:

```java
import java.util.Stack;

public boolean isCodeBlock(String markdown, String possibleLink) {
    int idxOfLink = markdown.indexOf(possibleLink);
    Stack<Integer> codeSignaler = new Stack<>;
    int currIndex = 0;
    while (currIndex < idxOfLink) {
        int codeSignalerIdx = markdown.indexOf('`', currIndex);
        if (codeSignaler.peek() != null) {
            codeSignaler.pop();
        }
        codeSignaler.push(codeSignalerIdx);
        currIndex = codeSignalerIdx;
    }
    return (codeSignaler.peek() != null);
}
```

This may have likely been over 10 lines of code (oops)! There is also the possibility that a \` may be within the Brackets, but are not complete (i.e. it continues outside of the link) which may create issues. This case is not covered by the implementation of the code above.

## Snippet 2

The issue with this snippet was that the second link, a.com(()) was being trimmed of half of its last ) as well as missing the last link. This was likely caused due to the multitude of parenthesis within a.com(()), thus my solution to the issue would require a validator of the amount of parenthesis within a valid url link. This may take more than 10 lines to implement as I would require a type of `parenthesisMatcher` method which may be best paired with a Stack data structure like above. As for the issue with escaped brackets, I am unsure if my `getLinks` method is having an issue with that as the bug with a.com(()) could explain why the escaped bracket links are not working.

## Snippet 3

The issue with the final snippet is that my implementation of `getLinks` lacks a way of validating and ensuring line breaks do not break the links which are getting parsed. This fix would require better understanding the way which line breaks are transcribed through Java Strings, thus it may require a code fix of larger than 10 lines as I do not have a current way of checking to see if lines are within the url snip.

