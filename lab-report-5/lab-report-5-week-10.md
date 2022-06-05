# Week 10: Lab Report 5

Welcome to my final lab report! This report goes over some of the final topics learned within the class regarding the utilization of `vim` and `bash` to compare implementations across many tests. 

Just some reminders: 
- My name is Nhan Quach
- My group leader is Elias
- My team members are as follows:


| Member 1 | Member 2 | Member 3 | Member 4 | Member 5 | Member 6 |
| -------- | -------- | -------- | -------- | -------- | -------- |
| Nhan     | Tyler    | Kayla    | Diego    | Jas      | Snehal   |

## Links to the Repositories for MarkdownParse

Mine: [ima_quack](https://github.com/ima-quack/markdown-parser)

Cloned: [nidhidhamnani](https://github.com/nidhidhamnani/markdown-parser.git)

---

# Finding the Varying Test-Results

In order to check the variations in test results, I utilized `bash` scripting methods in conjunction with `vimdiff`. First, I edited the `script.sh` file within the lab cloned [repository](nidhidhamnani/markdown-parser) by adding in an `echo $file` to print out the file name for each ran test case. 

![echo](images\script_change.png)

Afterword, I utilized the copy `cp` command to copy over that `script.sh` file into my directory with my version of `MarkdownParse.java`. 
I ran the script utilizing bash commands and redirected the output to a text file utilizing `bash script.sh >> results.txt` on both my directory and the cloned one. 

Finally, I utilized `vimdiff` on my version’s results.txt and the cloned repository’s. 

![vimdiff](images\vimdiff.png)

The left-hand side is the results from running `MarkdownParse.java` on the original repository from [nidhidhamnani](https://github.com/nidhidhamnani/markdown-parser.git) while the right-hand side is the results from running it on my [repository](https://github.com/ima-quack/markdown-parser).

The specific tests I utilized were test case [**22**](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/22.md?plain=1) linked [here](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/22.md?plain=1) and test case [**194**](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/194.md) linked [here](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/194.md) which images will be included on the bottom.

---

# Comparing Test 22:

![test22](images\test22.png)

Reminder, left-hand side is from the original forked repository, and the right-hand side is from my implementation. [Link to test](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/22.md?plain=1)

According to the CommonMark demo [website](https://spec.commonmark.org/dingus/), the correct output should be along the lines of `[/bar\* “ti\*tle”]`. Note, that I held some skeptism over the results, so I added in an example which would clearly be a link called "thing".

![links](images\link.png)
![linkProof](images\linkProof.png)

In both cases, the **foo** behaved exactly like a normal link.

Under this case, my implementation was able to properly catch this test. 

The bug in this case stems from how the cloned repository only adds in a link when there are no spaces within the `[ ]`. Logically, this makes sense as we expect our links to not have any spaces within them, however in this scenario, a space exists due to the regex wildcard search `\*`. A fix could be implemented such that following a `\`, the `MarkdownParse.java` should investigate to see whether or not there are regex symbols.

![repo_change](images\cloneHighlight.jpg)

---

# Comparing Test 194:

![test194](images\test194.png)

Reminder, left-hand side is from the original forked repository, and the right-hand side is from my implementation. [Link to test](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/194.md)

According to the CommonMark demo [website](https://spec.commonmark.org/dingus/), the correct output should be `[url.com]`. 

![link2](images\link2.png)
![link2Proof](images\link2Proof.png)

Under this case, the clone’s implementation is correct. 
The bug within my version of `MarkdownParse.java` might stem from the way which Markdown incorporates self-reference links within the document where something can be created to a link to a section or something of the like by adding `[]:`.

According to this github [site](https://github.com/Python-Markdown/markdown/blob/master/docs/extensions/abbreviations.md), these are abbreviations which provide definitions for certain parts of the document. 
One thing I could possibly do is add an array and place in any words within `[ ]` if it is followed by a `:` then check to see if there are valid text following the `:`. If the word appears again within the document, I could compare it with the array storing abbreviations to make sure it exists and skip the various additional checks for links. 

![mine](images\mine.jpg)