---
layout: post
title: ".zip and Hash[] are Really Handy"
date: 2013-10-18 01:07
comments: true
categories: [".zip, Hash[], Ruby, methods"]
---

We're wrapping up week 4 at the Flatiron School and... I'm starting to work on a fun gem idea! Yes, I've been inspired by my classmates to take the plunge and build my own Ruby gem. 

But first things first. I need data in order for my gem to be useful. So earlier today (well, yesterday, at this point) -- I proceeded to scrape some data. And in the process, I discovered a neat pair of methods that work very nicely together: .zip and Hash[].

<h4>WHAT DOES .ZIP DO?</h4>

The .zip method basically joins two arrays together, pairing elements from each that have matching indexes and returning the whole thing as a big array that contains mini-arrays populated with the newly paired elements. You set one of the arrays as the receiver of the method, which then takes the second array as an argument. It looks something like this:

`array1.zip(array2)`

Not too complicated, right?

Here it is in action:

``` ruby
array1 = [1, 2, 3]
array2 = ["apple", "orange", "banana"]

array1.zip(array2)
=> [[1, "apple"], [2, "orange"], [3, "banana"]]
```
<br>

<h4>WHAT DOES HASH[] DO?</h4>

The Hash[] class method is SO cool. You can basically dump the whole `array1.zip(array2)` sequence inside of the [brackets], like so:

`Hash[array1.zip(array2)]`

What do you think this will result in?

Only one way to find out!

``` ruby
array1 = [1, 2, 3]
array2 = ["apple", "orange", "banana"]

Hash[array1.zip(array2)]
=> {1=>"apple", 2=>"orange", "3=>banana"}
```
<br>

How crazy awesome is that?! It returned a hash and populated it with key-value pairs made out of the elements from each array that have matching index numbers. 


So the .zip and Hash[] methods, together, proved very useful indeed as I scraped data from Billboard.com and was able to get `artists` and `songs`, separately, to look like a numbered list of the pair, `artist - song`. And that's all I'm saying about my gem-in-progress, for now! 

I <3 Ruby.


<h4>KEY TAKEAWAYS</h4>
1. You can join two arrays together and return matching-index pairs using `array1.zip(array2)`
2. You can create a hash populated with key-value pairs made out of two arrays using `Hash[array1.zip(array2)]`

