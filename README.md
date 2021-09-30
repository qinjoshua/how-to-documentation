# How-To Guide: Developer Documentation
By Joshua Qin - 38 minute read
## Who this guide is for
This guide is for beginner programmers who already have some experience writing code. You may have started to dip your feet into writing code, and you're beginning to to think about building bigger projects. At this point, you've heard about documentation before, and you've seen some examples of it in practice. You've seen user manuals, guides, code snippets, or developer resource pages with examples of documentation embedded in it.

This guide is also for those who have built complex projects, but only individually. You want to see how code can scale to teams, or you would like to release your projects to the general public. You want to share your project with other people, so that they may add to it, refer to it, or use it.

In this guide, we will cover what code documentation is, and emphasize the need for proper documentation. We will tell you about the best practices for documentation, drawing on real resources from some of the largest software companies in the industry. All throughout this guide, we will go over specific examples, so you may see what documentation looks like in a codebase, and in a production project.



## Introduction to code documentation

### What is code documentation?

Developer documentation is one of to types of information about your coding project: *what something does*, or *how something should be done*.[^2.1]

Typically, that "something" will be code. A code snippet that does complex logic may have **code comments** next to each line, walking through the semantic meaning of the code. However, that "something" could refer to other parts of the project as well. For example, an API may describe function headers and an explanation of their purposes. Such are cases of describing "what something does".

Alternatively, documentation can describe how something should be done. A testing **specification** explains in detail how the testing process for a certain project should be conducted. For released projects, a piece of software may include a **user manual** that instructs the end user how the software should be used. These examples constitute "how something should be done."

#### Documentation is not formal writing

Although there are best practices and guidelines to follow, *documentation is not formal writing*. You may have heard that using pronouns, citing Wikipedia, or using certain terms would be frowned upon in formal writing. None of these traits apply to documentation writing.

Documentation writing should be straightforward, succinct, and convey the most important information as fast as possible. If a thought can be adequately expressed in sentence fragments instead of grammatically correct full sentences, use sentence fragments. When necessary to convey a message, using emotional writing or even swearing can be allowed (albeit under very specific circumstances - we do not endorse swearing to get your point across). Pragmatism is key.

#### Self-documenting code

Sometimes, your project may be **self-documenting**, when the questions of "what something does" or 
how something should be done" are obvious enough without needing additional documentation. For example, a function called `convertIntegerToBinary` has a fairly unambiguous purpose.

Other examples of self-documentation include UI that is obvious enough to use without a manual, or programmed constraints that force a certain pattern of behavior.

##### Is self-documenting good enough?

Take our example above of the unambiguous function name. Is a code comment, or an entry in a manual, still necessary to describe the functionality in this case?

Proponents of self-documenting code as a replacement to formal documentation, also known as **extreme programming**, argue that self-documenting code is faster for both the developers and the users, saves time, and reduces bloat on formally documented code.

As we will review later in this guide, not all code needs to be documented. That being said, when in doubt, it is always safer and better to document more in the present than to wish you had documented more in the future.[^2.2]

Documentation may also include crucial details that self-documenting code simply cannot capture. Jef Raskin[^2.3] once wrote:

> But the fundamental reason code cannot ever be self-documenting and automatic documentation generators can’t create what is needed is that they can’t explain why the program is being written, and the rationale for choosing this or that method.

You should always strive to make your projects self-documenting. Explanations written for humans to read is no substitute for properly named variables or methods that describe exactly what they represent, at a glance.

### Why document your code?

If you are reading this guide, you've already reached the stage where you are planning on having others interacting with your code. At this point, it becomes critical that code is well-documented so that others can pick up and understand your code without needing to ask you for clarification.

Program code exists in an intermediate stage between human language and machine language. Pure machine language is impossibly tedious to read by humans, and human languages are unintelligible to machines. Although program code is readable by humans (and improving all the time), it is still structured in such a way that it must be able to be compiled into commands that can be loaded or interpreted by a machine. The logic may make sense to the writer at the time of writing, but it can and often is difficult to follow by other parties who have not already formed the mental model of how code should work.

Documentation isn't just important for others, either - it should be important to the code writer as well. [^2.4]

**Eagleson's Law**[^2.5] states that:

> Any code of your own that you haven't looked at for six or more months might as well have been written by someone else.

At the time of writing, it's quite possible that you understand the code that is written fully, with a complete mental model of the code well-fleshed in your mind. Over time, as you work on other code, you will forget that mental model. Without documentation, looking back on even your own code will force you to recreate that mental model from scratch.

[^2.1]: Boersma, Eric. “Code Documentation: The Complete Beginner's Guide - Submain.” *Code Documentation: The Complete Beginner’s Guide*, SubMain Software, 11 June 2019, https://blog.submain.com/code-documentation-the-complete-beginners-guide/.
[^2.2]: Stephens, Matt, and Doug Rosenberg. *Extreme Programming Refactored: The Case against XP*. Apress, 2003.
[^2.3]: Raskin, Jef. “Comments Are More Important Than Code.” *Comments Are More Important than Code - ACM QUEUE*, 18 Mar. 2005, https://queue.acm.org/detail.cfm?id=1053354.
[^2.4]: Jones, Matthew. “Ancient Oracle, Modern IIS, and a Failure to RTFM.” *Exception Not Found*, Exception Not Found, 21 Mar. 2016, https://www.exceptionnotfound.net/ancient-oracle-modern-iis-and-a-failure-to-rtfm/.
[^2.5]: Eagleson's law is often cited, but who Eagleson actually was remains a mystery. The earliest known attribution was in 1987, on a USENET forum comp.fortune file. Some [forums](https://ask.metafilter.com/200910/Who-is-Eagleson-and-where-did-Eaglesons-law-originate) theorize that the quote was self-attributed a long time ago, and has simply remained in use since. Here is a link to one article that references Eagleson's Law: Reed, Niamh Isobel. “Ten Laws of Software Development.” *Medium*, Product Coalition, 12 June 2019, https://productcoalition.com/ten-laws-of-software-development-cbd72db0f85c.



## Types of documentation

We've already mentioned a few common types of documentation - code comments, user manuals, specifications. Here, we list a few more examples that show the diversity and prevalence of documentation in the developer process.

| Documentation Type      | Description                                                  |
| ----------------------- | ------------------------------------------------------------ |
| Code Comments           | Comments included in-line within a code file, describing the function of the immediate code around it. Code comments can be used to describe the function of blocks of code, explain very complicated code segments, or breakdown unclear or counter-intuitive individual lines of code. Most programming languages provide [some way](http://www.gavilan.edu/csis/languages/comments.html) to include code comments directly into the source code, using special symbols to indicate that the comments were meant to be ignored by the compiler. Examples: `// C comment` `# Python comment` `<!--HTML comment-->` |
| User Manual             | Instructions meant to be read by the end user, typically included in released versions of software delivered to customers. User manuals can take many forms: manuals may be a straightforward description of the functionality of a product, list different functionalities and how they may be used, or provide step-by-step tutorials for users, especially for beginner users. In the past, physical user manuals were included in boxed copies of software; nowadays, user manuals are typically found online. Also see: [Example of user manual](https://www.hmisource.com/otasuke/files/manual/pl_option/XPE-MM01-PDF-eng.pdf), [General guide to formatting user manuals](http://www.hpandt.com/howtocreateeffectivetrainingmanuals.pdf) |
| Process Documentation   | Guide to a process, typically for internal use. Many development projects in large teams are process-intensive, which can be unfamiliar to new workers on a team. Process documentation can be used to describe a wide range of activities including testing, release, code verification, bug reporting, version control, reporting, designing, or code writing. For example, a release doc might describe the steps that should be taken to ensure that a release is stable, how to build the release version of a software, and how to ship the software to end-users. |
| Specifications          | Details how a project should work. Colloquially referred to as "specs", it can commonly be used to outline the characteristics of a project or task, which are requirements that are utilized to build the project. Specifications are important to plan out the high-level picture of any project, and allows managers and stakeholders to communicate their needs to the developers to be implemented. |
| Release Notes           | Shows the end-user or internal development teams what features are in a release, or what changes have been made since the last release. Also commonly termed "changelog". Release notes serve a multitude of purposes, from tracking when releases were added, to notifying end users of what to expect different from an update. [Example of release notes](https://docs.microsoft.com/en-us/windows/release-health/release-information) |
| Technical Documentation | Explains parts of software code in an external format, as opposed to being in-line like code comments. For example, a readme file or a listing of API headers. Embedded technical documentation is technical documentation that is generated by an automated tool from code comments. Certain comments can be automatically transformed into a richly formatted documentation format, usually exported as HTML. Comments at the top of each function, for instance, could be transformed into a table listing the function header and its functionality. Examples of embedded technical documentation generators include [Javadocs](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/javadoc.html), [JSDoc](https://jsdoc.app/), and [Sandcastle](https://www.microsoft.com/en-us/download/details.aspx?id=10526) |
| Architecture Design     | Describes the technical design of a project, as opposed to specifications, which detail only the high-level requirements from a less technical perspective. Architecture design documentation will show how individual components of a complex project fit together and interact. For example, database entity relationship diagrams show how tables interact with one another, and what fields go in each table. [Example of database ERD](https://www.conceptdraw.com/How-To-Guide/erd-entity-relationship-diagram-examples) |
| Sales Documentation     | Documentation used to highlight features to the customer, used by sales and marketing professionals in order to sell the product. Unlike technical documentation or user manuals, sales documentation are not meant to be comprehensive. Instead, sales documentation is designed to underscore selling points and provide enough relevant information to help customers decide on which product to use. |

For technical documentation and other quick and easy types of documentation, Markdown is a fantastic tool to use for the job. Markdown is well-known by most programmers, supported by popular programming tools like GitHub, very easy to create and edit, and already commonly used by software developers. This very doc is written in Markdown, for example.



## Documentation best practices
Different types of documentation will have different writing styles. The most common type of documentation are code comments; however, I will also briefly touch on other types of documentation, and describe general best practices to follow for all types of software documentation.

### Code comments

In this section, I will be going over several recommended practices[^4.1][^4.2] [^4.3]for writing code comments.

#### Where should code comments be used?

##### Where code logic is unclear

Comments can be used to explain, in human terms, what a chunk of code is doing. Take the following example, [from MSDN](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/working-with-linq):

```c#
public static IEnumerable<T> LogQuery<T>
    (this IEnumerable<T> sequence, string tag)
{
    // File.AppendText creates a new file if the file doesn't exist.
    using (var writer = File.AppendText("debug.log"))
    {
        writer.WriteLine($"Executing Query {tag}");
    }

    return sequence;
}
```

As you can see in this sample, there is a brief code comment mentioning that `File.AppendText` will create a new file, if one does not already exist. This kind of functionality isn't self-documenting; nothing about the name `File.AppendText` indicates that it also has the ability to create a new file. Notice that the comment does not mention that `File.AppendText` will append text to a file, because that much is already self-evident.

Now take this somewhat more complicated example, taken from a C++ merge sort implementation from [tutorialspoint](https://www.tutorialspoint.com/cplusplus-program-to-implement-merge-sort):

```c++
void merge(int *array, int l, int m, int r) {
   int i, j, k, nl, nr;
   //size of left and right sub-arrays
   nl = m-l+1; nr = r-m;
   int larr[nl], rarr[nr];
   //fill left and right sub-arrays
   for(i = 0; i<nl; i++)
      larr[i] = array[l+i];
   for(j = 0; j<nr; j++)
      rarr[j] = array[m+1+j];
   i = 0; j = 0; k = l;
   //marge temp arrays to real array
   while(i < nl && j<nr) {
      if(larr[i] <= rarr[j]) {
         array[k] = larr[i];
         i++;
      }else{
         array[k] = rarr[j];
         j++;
      }
      k++;
   }
   while(i<nl) {       //extra element in left array
      array[k] = larr[i];
      i++; k++;
   }
   while(j<nr) {     //extra element in right array
      array[k] = rarr[j];
      j++; k++;
   }
}
```

In this example, complex calculations like `nl = m-l+1; nr = r-m;` are explained with comments, as well as all of the loops. In these cases, the reader can't tell at a glance why the calculation is done in that way, or what purpose the loop serves. For a complex algorithm like this, it is best to break down what each chunk of non-trivial logic does, so that the user is able to better follow the algorithm.

###### A brief note on variable naming and self-documenting code

The merge sort example also makes use of single letter or abbreviated variable names. Doing so trades code readability for brevity, with comments added to help clear up confusion. Whether or not this should be considered a best practice is subject to [*intense* debate](https://stackoverflow.com/questions/5802403/using-single-characters-for-variable-names-in-loops-exceptions) that is thankfully beyond the scope of this guide. Our recommendation is that variables should generally be longer than a single character and should explain itself, except for the cases of coordinates (ex: `x, y, z`), exception names, (ex: `Exception e`), loops (ex: `for i from 0 to 10`), and lambda functions (ex: `((λ(x) x) 10)`).[^4.4]

##### Where code rationale/purpose is unclear

In some cases, the reason why a piece of code exists is unclear. In other cases, there may be some backstory to the code that isn't clear at a glance. In these cases, it's useful to have comments that give information about the rationale of the code.

The following code, [from Stack Overflow](https://stackoverflow.blog/2021/07/05/best-practices-for-writing-code-comments/), shows off how code comments can be used to explain a bug:

```java
  // NOTE: At least in Firefox 2, if the user drags outside of the browser window,
  // mouse-move (and even mouse-down) events will not be received until
  // the user drags back inside the window. A workaround for this issue
  // exists in the implementation for onMouseLeave().
  @Override
  public void onMouseMove(Widget sender, int x, int y) { .. }
```

Here, we show a perfect example of an explanation for the reason why this workaround exists and the history of the issue it is trying to solve. Now, if someone ever fixes the root cause of this bug, looking at this code comment can indicate to the programmer that this workaround can now be removed.

Without these kinds of comments, codebases tend to rot over time. Pieces of code that look unused, or are not used in any obvious way, are left behind. Without context, future users may simply delete the code with [unexpected consequences](https://www.thegamer.com/this-coconut-jpg-in-team-fortress-2s-game-files-if-deleted-breaks-the-game-and-no-one-knows-why/). Far worse, however, is that future users may be too afraid to ever touch it, leaving legacy code permanently embedded into the project, potentially contributing to bugs or slowdowns into the far future.

Here is the [single best example](https://pastebin.com/PTLeWhc2) that both illustrates the importance of writing down code rationale in comments and serves as a rationale comment in itself:

```c++
    if (rMsg.message == WM_TIMER && rMsg.hwnd == NULL) {
#ifdef CHICAGO_PRODUCT
        /* The reason for requiring the following test is now lost
         * in the mists of time.  Now this app is 32-bit, these
         * bogus timer callbacks (if they really do still occur)
         * could be 16-bit, so we need to add yet more ugliness
         * in the form of assembler to an app which is already
         * hardly a paragon of pulchritude.
         *
         * A plea:
         *
         * If you add some obscure code such as below, to this or
         * any other app, even if it has only the teeniest chance
         * of being less blindingly obvious to someone else than
         * it is to you at the time of writing, please please please
         * add a f***ing comment.
         *
         * Respectfully,
         * A Developer
         */
```

This was a comment found in leaked copies of the official Windows XP source code, an operating system that was used in well over one billion computers.

         * in the mists of time.  Now this app is 32-bit, these
                  * bogus timer callbacks (if they really do still occur)
                  * could be 16-bit, so we need to add yet more ugliness
                           * in the form of assembler to an app which is already
                           * hardly a paragon of pulchritude.
                                    *
                                    * A plea:
                                             *
                                             * If you add some obscure code such as below, to this or
                                                      * any other app, even if it has only the teeniest chance
                                                      * of being less blindingly obvious to someone else than
                                                               * it is to you at the time of writing, please please please
                                                               * add a f***ing comment.
                                                                        *
                                                                        * Respectfully,
                                                                                 * A Developer
                                                                                 */

##### Where you need to cite or specify the ownership of the code

Comments can also be used to input legal warnings, attribution, or specify authorship/ownership of a piece of code. In some cases, this is necessary for legal reasons. In other cases, developers may want to give credit to an original source, or simply cite a resource so that future developers have something to refer to.

The following is an example of a simple code attribution to an article [originally written](https://www.c-sharpcorner.com/blogs/drag-and-drop-file-on-windows-forms1) on C# Corner:

```c#
// The following code was written by André de Mattos Ferraz on C# Corner. Thanks André!
// https://www.c-sharpcorner.com/blogs/drag-and-drop-file-on-windows-forms1
private void textBox1_DragOver(object sender, DragEventArgs e)  
{  
   if (e.Data.GetDataPresent(DataFormats.FileDrop))  
      e.Effect = DragDropEffects.Link;  
   else  
      e.Effect = DragDropEffects.None;  
} 
```

Now if anybody had any questions about what other methods this code played into or why and how this code was written, that person can simply go to the link and read the full tutorial.

The following is an example of a copyright code snippet, taken from UC Berkeley:

```python
# ---------------
# Licensing Information:  You are free to use or extend these projects for
# educational purposes provided that (1) you do not distribute or publish
# solutions, (2) you retain this notice, and (3) you provide clear
# attribution to UC Berkeley, including a link to http://ai.berkeley.edu.
# 
# Attribution Information: The Pacman AI projects were developed at UC Berkeley.
# The core projects and autograders were primarily created by John DeNero
# (denero@cs.berkeley.edu) and Dan Klein (klein@cs.berkeley.edu).
# Student side autograding was added by Brad Miller, Nick Hay, and
# Pieter Abbeel (pabbeel@cs.berkeley.edu).
```

The licensing information clearly lists the authors, how the code can be used, and information about how the code should be attributed.

###### Citing Stack Overflow

A lot of developers copy code from the internet.[^4.5] There is nothing wrong with copying code that other people have written, except legal provisions may apply. Stack Overflow is by far one of the most popular developer Q&A forums, and unbeknownst to many developers, there are guidelines set forth for attribution of code copied from Stack Overflow. For more information, see [Stack Overflow's attribution policy](https://stackoverflow.blog/2010/08/11/defending-attribution-required/).

##### Where you want to put a placeholder for code yet to be written

One common use for documentation comments is to write out temporary comments for where code should go, when it gets written in the future. An example of this is as follows:

```javascript
var stringNormalizer = function(var input){
	// This function only returns the original input. Once
    // string normalization is finished, please write it here
	return input;
}
```

In this case, the `stringNormalizer` function is just a stub. Without this comment, it's possible that a future user could overlook this function and assume it already works, or perhaps write another function for string normalization elsewhere.

In most IDEs, the use of the word `TODO` in comments will create a special flag that allows you to easily find and jump to that comment. In development, this is extremely useful because it allows you to put down scaffolding before writing individual implementations. Writing `TODO` statements also provides you the ability to document all the unfinished portions of your code, so that nothing is missed.

##### Where you are writing tutorials/how-tos

This case is special. When you are writing tutorials, reference guides, or anything where the code is meant to be copied or scrutinized by a new user, include as many comments as necessary to explain every step of the process. Where normally in a production code base commenting each step could be considered overly verbose, in a learning environment this is absolutely necessary.

The following is an example of mergesort implemented in java, [from Stack Overflow](https://stackoverflow.com/questions/17978334/implementing-merge-sort-in-assembly):

```java
// sort the subarray arr[i]..arr[j]
void mergeSort(int &arr, int i, int j)
{
if (i == j) return;          // terminating condition
int m = (i+j)/2;             // Step 1: compute the splitting point
MergeSort(arr, i, m);        // Step 2: sort the left part
MergeSort(arr, m+1, j);      // Step 3: sort the right part
Merge(a, i, m, j);           // Step 4: merge the sorted parts
}
```

Here, inline comments are employed to describe every step of the process, which would almost certainly be too verbose to use in any other setting.

#### Where should code comments NOT be used?

##### Where it's glaringly obvious

My computer science teacher once told our class:

> You will never be penalized for writing too many comments

While he was right to encourage code commenting, something that all programmers should get into the habit of doing, these instructions - often repeated in programming classrooms around the world - encouraged poor commenting behaviors that would not be acceptable in production code. Such a thing as writing too many comments exist.

An example:

```batch
IF EXIST "file.ext" (
REM if the code enters here, this means that the file has been found
ECHO file found
) ELSE (
REM tell the user an error has occurred if file has not been found
ECHO Error: file not found
)
```

While this seems, well, glaringly obvious, in practice it may be tricky to determine what comments are obvious and what comments are not. Some inexperienced users may find certain function calls to be non-obvious, whereas in reality those function calls can be commonly used in the codebase. Providing detailed information in a comment next to each function call is too cluttering for those comments to be useful.

In general, read the code over in your head before you add comments. If the code makes sense just by reading it out loud, it likely doesn't require commenting. Remember, time spent writing comments is time not spent writing code. Additionally, adding unnecessary comments actually make code more difficult to read. In the example above, a perfectly readable block of code has been interrupted with unnecessary comments that serve no purpose but to distract the programmer.

##### Where there are too many comments already

When there are already many comments in a block of code - for example, one across every line - summarizing those comments or making your code clearer in the first place is usually the best idea. Even when the code isn't glaringly obvious, adding comments between every line is intrusive. Doing so prevents developers from easily skimming or modifying existing code.

Another common problem to avoid would be including too many comments in the heading banner of a code file. Including some information about copyright, attribution, authorship, and what the code is about is usually fine. But, including a full changelog, detailed descriptions of every variable, or even including in a full user manual right into the comments of the code is almost certainly excessive.

This example comes from [youtube-dl](https://github.com/ytdl-org/youtube-dl/blob/master/youtube_dl/YoutubeDL.py):

![image-20210924212637944](https://i.ibb.co/L5JctqP/image-20210924212637944.png)

As you can see, the header comment includes not only a complete description of the product, but also a listing and description of every available parameter. Information like this should go into its own readme or manual, and should not be embedded into the source code of the project.

##### Where comments substitute for self-documenting code

Earlier, we mentioned that the first instinct any programmer should have writing code is to make their code as self-documenting as possible. Writing comments can help fix code that has no choice but to be complicated or unclear, but comments should not be used to patch up poorly written code. Donald Norman, author of "The Design of Everyday Things," pointed out that signs are often overused to cover up poor physical design. Code documentation may inevitably serve a similar purpose, unless the code writer takes preventative measures.

If you find yourself in a high comment to code ratio, you may need to **refactor** your code. Here are some common techniques for doing so:

- Change variable names so that they make sense. For instance:

  ```c#
  var pfc = 50; // Represents the player's position from the center of the screen
  ```

  can be refactored into the following:

  ```c#
  var posFromCenter = 50;
  ```

  - A rookie mistake is to give variables quick and fast names for the sake of saving time, like calling variable names `x1` or `x2`. You *will* forget what this is supposed to mean in the future.

- Take out magic constants, and store them in their own variables. For instance:

  ```C#
  var positionFromCenter = 50; // 50 is the default position
  ```

  can be refactored into the following:

  ```c#
  const int DEFAULT_POSITION_FROM_CENTER = 50;
  var positionFromCenter = DEFAULT_POSITION_FROM_CENTER;
  ```

- Rename functions or methods so that they make grammatical sense when chained to other functions or methods. You should try to have your code read as close as possible to human language. For example:

  ```c#
  // Moves the player to the given x and y coordinates
  public void movePlayer(int x, int y) {
  	[...]
  }
  
  Player.movePlayer(25, 25);
  ```

  can be refactored into the following:

  ```c#
  public void moveTo(int x, int y) {
  	[...]
  }
  
  Player.moveTo(25, 25);
  ```

- Take out blocks of codes denoted with "Begin" and "End" comments, and put them into their own methods. For instance:

  ```c#
  public void moveTo(int x, int y) {
  	List<PlayerComponents> playerComponents = new List<PlayerComponents>();
  	// Begin logic to get all components of a player that should move
  	playerComponents.add(this.head);
  	playerComponents.add(this.torso);
  	for (int i = 0; i < player.itemsHolding; i++)
  		playerComponents.add(this.itemsHolding[i]);
  	// End logic to get all components of a player that should move
  	[...]
  }
  ```

  can be refactored into the following:

  ```c#
  public void moveTo(int x, int y) {
  	List<PlayerComponents> playerComponents = getPlayerComponents();
  	[...]
  }
  
  public List<PlayerComponents> getPlayerComponents() {
  	List<PlayerComponents> playerComponents = new List<PlayerComponents>();
  	playerComponents.add(this.head);
  	playerComponents.add(this.torso);
  	for (int i = 0; i < player.itemsHolding; i++)
  		playerComponents.add(this.itemsHolding[i]);
  	return playerComponents;
  }
  ```

  This way, complex logic can be wrapped in self-documenting functions, and the logic can be easily modified or reused without breaking the rest of the program.

##### Where comments serve no other purpose than to be witty or mean

Even though documentation is not formal writing, it should at least still be professional. After all, this is code intended for others to read. Previously, I mentioned that emotional writing or even swearing could be acceptable as long as the message was most effectively conveyed. However, there are obviously limits to how these elements should be used.

Think about it in terms of how you would speak to a colleague while explaining the code. If your opinionated or informal language would be the most effective way to speak to a colleague, write it like that in the code. However, if you're just trying to be funny, or if you're downright demeaning to other code-writers, it would be best for you to keep those comments out.

In the early days of Microsoft, programmers reportedly put a great deal of profanity and snarky comments into their code writing[^4.6]. While funny, the source code has now been released to the public and the idea of one of the most powerful tech companies in the world writing comments like this is a bit ridiculous:

```assembly
; DH  will contain internal flags
; BP  is used as always, the other registers are free to fuck with.

	push	bp
	mov	bp,sp
	add	sp, local_space
```

```assembly
; Assemble Note: coded inline because we're gods

	lea	si,	[rcwClipXpLeftRc]
	cmp	[vfPrvwDisp],fFalse
```

At best, it's a waste of space. At worst, it could create a toxic workplace environment and hurt relationships to other code writers on the team. Just get the message across; don't be clever with your comments.

#### Matters of controversy

There is no one set of best practices for how code comments should be used. Ideologues exist from across the coding world with their own opinions on how code should be documented, which is why some of the differing opinions are included below.

##### Agile development

**Agile** is a development methodology that revolves around a set of values and principles, designed to make software development faster and more flexible than older models of work. One of the primary values is as follows[^4.7]:

> Working software over comprehensive documentation

Some interpretations of this line is that time should not be wasted on meticulous documentation, in favor of writing working code first. However, interpretations of how this value should be applied differ.

The Agile manifesto also includes this addendum:

> That is, while there is value in the items on the right, we value the items on the left more.

In short, this means that documentation is still necessary and valued[^4.8]. Agile seeks to address the shortcomings of the waterfall development method, in which huge projects were planned from the beginning and developed in isolation, with a strict set of protocols to dictate the development lifecycle. To do this, Agile emphasizes working on small components first, and constantly receiving user feedback. Documentation in an Agile setting, while not as burdensome and resistant to change as in waterfall, should take this into account.

##### Inline comments

**Inline comments** are comments that are written in the same line as code. In line comments are generally very short, and exist only to provide a little bit of context where it would be wasteful to use a full line.[^4.9]

Proponents of inline comments argue that allocating whole lines to very small comments that generally only apply to a single line of code can be misleading, or make the source code appear too bloated. Opponents argue that inline comments are often used to cover up poorly written code that could be self documenting, and are often abused because of they are incorrectly perceived to be unintrusive.[^4.10]

### Other types of documentation

#### User manuals

At most companies, user manuals are written by dedicated **technical writers** who are responsible for taking the instructions that programmers use and turn it into readable instructions that can be passed off to the customer.

Unlike code comments, user manuals are more formal, and do not typically suffer from being too verbose. Because programmers are familiar with their own product, and tend to speak in concise terms that only other programmers on the project may understand, it is generally good practice to have technical writers take care of the production of user manuals.[^4.11]

#### Technical documentation

Technical documentation like javadocs, sandcastle, etc. occupy a space between user manuals and code comments. Like code comments, technical documentation is often embedded into code as it is written. Like user manuals, technical documentation is viewed by the end user, not necessarily for internal use. What sets technical documentation apart from other code comments is that technical documentation has a specific format that needs to be conformed to in order for tooling to generate the external files, from which they are ultimately delivered.

Technical documentation should be consistent across the project. If your team sets a policy to write technical documentation over every method and every class, then make sure that every method and every class is documented, even if it seems overly verbose. If there is a specific style of speech that you would like technical documentation to be written in, then make sure all the technical documentation.

#### Sales documentation

As in the case of user manuals, sales manuals are usually written by dedicated sales engineers. Sales engineers should be putting themselves into the shoes of a potential client, removing themselves from the technical considerations of the development team and only considering the technical considerations of a prospective customer. Sales documentation is allowed to be more boastful about accomplishments and features, and is not meant to be comprehensive.

### References

[^4.1]: Keeton, BJ.“How to Comment Your Code like a pro: Best Practices and Good Habits.” *Elegant Themes*, Elegant Themes, 24 Sept. 2021, https://www.elegantthemes.com/blog/wordpress/how-to-comment-your-code-like-a-pro-best-practices-and-good-habits.
[^4.2]: Fuex, John. “5 Best Practices for Commenting Your Code.” *Improving Software*, Improving Software, 3 Apr. 2015, https://improvingsoftware.com/2011/06/27/5-best-practices-for-commenting-your-code/#:~:text=5%20Best%20Practices%20for%20Commenting%20Your%20Code%201,control%205%20%285%29%20Comments%20are%20a%20code%20smell.
[^4.3]: Spertus, Ellen. “Best Practices for Writing Code Comments.” *Stack Overflow Blog*, Stack Overflow, 14 July 2021, https://stackoverflow.blog/2021/07/05/best-practices-for-writing-code-comments/.
[^4.4]: Zeunert, Matt. “Using Single-Letter Variable Names.” *JavaScript Code Readability*, JavaScript Code Readability, 2 Aug. 2015, https://www.codereadability.com/i-n-k-single-letter-variable-names/.
[^4.5]: Sinclair, Ben. “Do You Copy and Paste Code from Stack Overflow?” *DEV Community*, DEV Community, 1 Oct. 2018, https://dev.to/moopet/do-you-copy-and-paste-code-from-stack-overflow-47d5.
[^4.6]: Eadicicco, Lisa. “Microsoft Programmers Hid a Bunch of Profanity in Early Software Code.” *Yahoo! Finance*, Business Insider, https://finance.yahoo.com/news/microsoft-programmers-hid-bunch-profanity-191240410.html.
[^4.7]: Beck, Kent. Beedle, Mike. van Bennkum, Arie. Cockburn, Alistair. Cunningham, Ward. Fowler, Martin. Grenning, James. Highsmith, Jim. Hunt, Andrew. Jeffries, Ron. Kern, Jon. Marick, Brian. Martin, Robert. Mellor, Steve. Schwaber, Ken. Sutherland, Jeff. Thomas, Dave. "Manifesto for Agile Software Development." *Agile Manifesto*. [Manifesto for Agile Software Development (agilemanifesto.org)](https://agilemanifesto.org/).
[^4.8]: Friedrichsen, Uwe. *The Importance of Documentation*, 19 Mar. 2021, https://www.ufried.com/blog/documentation/#fn:1.
[^4.9]: Germain, H. James de St. “Commenting.” *Programming - Commenting*, School of Computing, University of Utah, https://www.cs.utah.edu/~germain/PPS/Topics/commenting.html.
[^4.10]: Dalling, Tom. “Why Inline Comments Are Generally a Bad Idea.” *Tom Dalling Blog*, 8 Oct. 1970, https://www.tomdalling.com/blog/coding-styleconventions/why-inline-comments-are-generally-a-bad-idea/.
[^4.11]: Hart, Geoffrey. *Why Do I Need a Technical Writer?*, https://www.geoff-hart.com/home/whytw.html#:~:text=Technical%20%20writers%20can%20write%20more%20concisely%20without,requirement%20for%20reviews%2C%20thereby%20%20reducing%20review%20costs.

