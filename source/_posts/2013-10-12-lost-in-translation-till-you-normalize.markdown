---
layout: post
title: "Lost in Translation - 'Till You Normalize"
date: 2013-10-12 23:33
comments: true
categories: [normalizing data]
---

This is something you're going to hear a lot over the course of your Ruby journey: "NORMALIZE YOUR DATA". But what does this mean?

Between humans, the concept of "normal" is typically (and overly-simplistically) understood to connote, "not weird". As in, if you're normal, then by default you are not a total weirdo (/ˈwi(ə)rdō/ 1. A person regarded as being very strange or eccentric 2. A deranged, potentially dangerous person. I suppose, however, that derangement and danger are not limited to just people).

In Ruby, on the other hand, "normal" -- or rather, "normalized" -- carries a very different meaning. The latter is mostly used to describe data (i.e strings, numbers, etc.) that has been transformed and accounted for in such a way that it is now easier to compare it against other data. It's kind of like assuring that nothing will be "lost in translation". In fact, it'd be a little like having a handy translator on hand (ha! no pun inten...) that can translate -- in real time -- whatever you're saying out loud in English to another language. And this might save your @$$ when you're trying to communicate to a room full of non-English speakers. IN FACT, when we humans translate stuff, we are, essentially, NORMALIZING it! 

Actually, I just thought of the best analogy of all: <u>it's making things "apples to apples"</u>. We couldn't run around comparing apples to oranges now, could we?!

<img src="http://www.foodrenegade.com/wp-content/uploads/2013/04/apples-a-year-old.jpg">


<h4>SOME COMMON METHODS USED TO 'NORMALIZE' DATA:</h4>

`.upcase` (capitalizes a string)<br>
`.downcase` (lower-cases a string)<br>
`.reverse` (reverses a string)<br>
`.sort` (sorts an array in ascending order, by default)<br>
`.split()` (splits a string per whatever you specify as an argument)<br>
`.gsub()` (substitutes all instances of one thing to another)<br>

<h4>SOME COMMON RUBY PROBLEMS THAT REQUIRE 'NORMALIZATION':</h4>

"Does Some_Array Contain an Anagram of a Given Word?" (can be nicely solved using `.sort`)<br>
"Is This_Sentence a Palindrome?" (might need a little`.downcase`, `.gsub` and `.reverse` action)<br>
"Deaf Grandma!" (a rare one that calls upon `.upcase`!)<br>
Dealing with user input in general via 'gets.chomp' or 'gets.strip' (always add a `.downcase` for good measure!)


Why that last piece of advice? Because every user on the planet can't be trusted to input his or her data accurately, every time. So 'normalizing' this input by calling `.downcase` on it ensures that you've accounted for any capitalization inconsistencies. You can now better compare apples to apples.



<h4>KEY TAKEAWAYS</h4>
1. 'Normalizing' your data means transforming its appearance slightly so that your program knows it's comparing apples to apples
2. Some common methods you can use to normalize data include:<br>
  `.upcase`<br>
  `.downcase`<br>
  `.reverse`<br>
  `.sort`<br>
  `.split`<br>
  `.gsub`<br>




