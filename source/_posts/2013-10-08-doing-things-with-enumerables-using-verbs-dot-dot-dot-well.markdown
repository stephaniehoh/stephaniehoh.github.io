---
layout: post
title: "Doing Things with Enumerables Using Verbs... Well, Methods"
date: 2013-10-08 03:28
comments: true
categories: [enumerables, methods]
---

A big thing for me as I make the transition away from my former life as an English and writing instructor is to make sense of coding by relating it to familiar concepts by means of analogy. 

So a big thing in Ruby is <b>methods</b>. Thus far, I've been thinking about methods <b>as if they were verbs in English</b> -- just like verbs describe actions, so methods let us act upon and DO things with objects. 

Now, a particular type of object called <b>Enumerables</b> has caused me some grief this past week, as it seems you can call upon an Enumerable an infinite list of methods. What are some examples of Enumerables? Well, basically any data structure that holds data and is therefore useful in Ruby -- two common ones being <b>arrays and hashes</b>. And thanks to David Grayson's Las Vegas Ruby Group presentation, <a href="https://speakerdeck.com/lvrug/rubys-enumerable-module-david-grayson">"Ruby's Enumerable Module"</a>, I now know that ranges, sets, String#chars, and String#bytes are also considered Enumerables. 

Grayson's deck is pretty straightforward -- no fluff, mostly examples of how an Enumerable might respond to or behave under a method. But this is great! Sometimes you get tired of consulting <a href="http://ruby-doc.org/core-2.0.0/">this</a> and it's nice to have found another source that really emphasizes <b>what the 'verbs', i.e methods, do</b>. Because let's face it. Without Enumerables and their corresponding methods, there's just... really not much else to do in Ruby. If you're not acting upon data by transforming/accessing/re-organizing/passing it around from one part of your program to another, then what are you doing? Right. And the only way you're going to accomplish any of the above is by taking advantage of all of Ruby's insane methods. 

So the most prevalent Enumerable method that I'd encountered way early on in my Ruby journey -- dare I say the most <em>commonplace</em> or <em>well-known</em> method -- is:

`.each`

Up until the end of last week, I tried to solve all my iteration problems using `.each`. And while the method does encompass the very spirit of iteration (how much more literal can it get than telling your program, "I want you to consider <b>each</b> thing and do what I say to it"???), relying on it for every scenario is like having one verb in your vocabulary and running around insisting that it should convey exactly what you mean, regardless of what it is you're trying to say (i.e "play!" to play, "play!" to eat, "play!" to sleep, "play!" to go home, "play!" to go to bed -- WHY WON'T ANYONE DO WHAT I ASK?!). It'd be ludicrous.

So I expanded my Ruby vocabulary the tiniest bit and discovered a few more Enumerable iterators that are SUPER useful, including:

`.collect` or `.map` (they do the same thing)<br>
and<br>
`.select`

(to grasp how useful `.select` is, just take a look at <a href="https://gist.github.com/stephaniehoh/6871313">this Anagram exercise</a> I solved in class yesterday)

Finally, in the wee hours of this morning/night, Grayson has introduced me to a few more iterators and methods that seem potentially very useful (and I can't wait to try them out tomorrow):

`.collect_concat`<br>
`.cycle`<br>
and<br>
`.group_by`

The last one, `.group_by`, I'm sure I've come across before but probably forgot existed. Just being honest.

<br>
<h4>KEY TAKEAWAYS</h4>

1. Methods are like verbs... you need to have a decent vocabulary of them, or else you'll be limited in how you can express yourself
2. Enumerables are pretty important in Ruby; they store data
3. Methods are also pretty important in Ruby; they let you access and manipulate the data stored in the Enumerables
4. Some cool iterators and methods you can call on Enumerables include:<br>
`.each`<br>
`.collect` or `.map` (they do the same thing)<br>
`.select`<br>
`.collect_concat`<br>
`.cycle`<br>
`.group_by`

