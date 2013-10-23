---
layout: post
title: "Git vs. GitHub for Dummies"
date: 2013-10-07 15:46
comments: true
sharing: true
categories: [git, github]
---

I meant to write this post last week, when I had my first Git/GitHub breakthrough. In my first post -- after Day 2 at Flatiron -- I bemoaned the fact that everything I'd attempted to absorb about Git and Github had, by the end of the day, turned into unpalatable git soup. A week later, after enough exposure and repetition (and causing one too many merge conflicts), I was able to strain some method out of the git soup-madness. 

Let's start by establishing a key concept: <b>Git and GitHub ARE NOT THE SAME THING</b>. 

They're not??? But, like, programmers refer to them (seemingly) interchangeably! 

Nope. Still not the same. They work hand in hand, but this doesn't equate to.... sameness. 

<h3>SO WHAT IS GIT?</h3>
Git can seem like total madness for a number of reasons, not the least of which because... well, GitHub's sheer existence. The latter has added a whole slew of very niche terminology to an already-extensive list of GIT-specific terminology: i.e, there's more shit to memorize. Anyway, you can think of Git as <b>a really awesome version-control software.</b> <b>You download it.</b> It lives <b>locally</b> on your computer. You run it <b>from your terminal</b>. You might be typing some Git-ish commands that look like this, from your command line:

`git init`<br>
`git add .`<br>
`git commmit -m "some witty message here"`<br>

If you are, then you're using Git -- NOT GitHub. 

And what exactly, by the way, is "version-control software"? It's basically just a handy program you install on your computer - just like when you download and install cool things like Skype - except you install Git from your command line. Which makes you really cool. Oh, and what it does: a million things. But two fundamental ideas are that:

1) <b>Git allows you to save different "versions" of your work as you go</b> -- via adds and commits. As long as you've installed Git on your computer and you do a `git init` in whatever directory you'll be doing your work, you can start saving versions of your work. And "work" really means anything; it could be Photoshop edits, essay drafts, spreadsheet modifications, you name it. It just so happens that if you're a programmer, you'll mostly be using Git to keep track of all your versions of code.

2) <b>Git lets you create and work on something called 'branches', which are basically parallel universes that you can switch back and forth out of interchangeably</b> -- via `git checkout <branch_name here>`. If that's still confusing to you, imagine if you could make as many copies as you wanted of your EXISTENCE, i.e seven different parallel universes, and in each of them, you can run around and live out a different version of your life that you've ever dreamed. When you feel like one particular universe has yielded the perfect outcome (you've become the next Jay-Z, met the man of your dreams, have been elected President of the United States), you can throw away the other six and decide "I ONLY WANT TO KEEP THE ONE WHERE I BECOME PRESIDENT." That's kind of how branches work. You get to make and work in as many as you want, and when you write code that you're happy with in any one of them, you can say, "THIS IS THE BRANCH I WANT TO KEEP" and throw the others away. 

Then we get into merging and pushing and some advanced Git topics that I'll chronicle in future posts (when I've actually wrapped my head around them). But this poses a natural segueway into GitHub.


<h3>COOL. NOW WHAT'S GITHUB?</h3>

Remember how I said Git lives locally on your computer? Well, GitHub is the exact opposite: <b>it lives remotely, on the Internet.</b> That's right -- as its name would suggest, GitHub is an online 'hub' that some really smart dudes built so that programmers could share their code remotely and collaborate on projects at the same time. It's kind of like the flashstick/Dropbox analogy -- sure, the flashstick was small and compact and mostly useful, but what if you wanted to access everything on your flashstick remotely? On the Internet? Especially if, like, you didn't have your flashstick with you?? Sorry, no can do. Until Dropbox came along! Suddenly, you could access ALL your files from any computer, as long as you had an Internet connection and as long as you'd explicitly added those files to Dropbox! Similarly, I like to think that GitHub is to Git what Dropbox is to the flashstick (yes, I know this is an oversimplification but if you just think about the remote-access part of the analogy, it works). 

So if you've got an Internet browser open, and you're typing "www.github.com" and hit enter, and you can see the Octocat mascot, you're using GitHub -- NOT Git. And why is this distinction so important? Well, that's like asking why it's important to understand that the files on your computer won't be accessible remotely unless you MAKE them 'remote' somehow, say, by uploading them to Dropbox. As long as you understand that <b>GitHub is a remote entity to which you're 'pushing' (i.e uploading) stuff that would otherwise only exist locally</b>, you're in good shape.

This will save you a lot of confusion and heartache down the road when you're wondering why stuff you're adding and committing locally isn't magically appearing online on GitHub (chances are, you did a `git init` locally first then forgot to create a 'pathway' between your computer and GitHub via `git remote add origin <some GitHub URL>`).

Anyway, I'll be doing more Git and GitHub posts down the road because I don't think any existing manuals on the Internet have really done an <em>excellent</em> job at illuminating how they work together (or explaining what they are, for that matter, hence this blog post). Even more egregious, in my opinion, is the lack of sensible visuals (most Git diagrams suck and have only confused me more) and the dearth in helpful analogies -- so I'll try to provide a little of both. 

<h4>KEY TAKEAWAYS</h4>

1. Git lives locally, on your computer
2. GitHub lives remotely, on the Internet
3. You can store and access your work online, on GitHub, but only if you EXPLICITLY SEND IT THERE -- i.e via a `git push` 
4. What you do locally on your computer doesn't just magically appear remotely online; you need to create the pathways and make the explicit commands
