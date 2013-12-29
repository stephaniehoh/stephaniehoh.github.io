---
layout: post
title: "The Ruby 'Struct' Class"
date: 2013-12-28 22:29
comments: true
categories: [ruby, struct, classes, POODR]
---

After months of hearing the book's name in mass circulation, I finally decided to get up close and personal with Sandi Metz' <em><a href="http://www.poodr.com">Practical Object-Oriented Design in Ruby</a></em>. I made this decision in part because the weeks leading up to Flatiron's graduation (Dec. 13th!) had been particularly Rails and JavaScript heavy, in part because this in turn had made me miss Ruby, and also in part because I felt it necessary to fortify my understanding of object-oriented programming best practices. 

Though I'm still in the early chapters of POODR, I can already tell this is going to be a monumental asset not only to my understanding and appreciation of Ruby, but also to my sensibilities and skills as a programmer. Most laudably, it's just written so damn well. Maybe too well, as <a href="http://ortask.com/book-review-poodr/">one reviewer</a> has tellingly marveled:

> "I was rather surprised how, even though the book starts with simple examples, it quickly develops and builds on them to provide good explanations." 

In other words, POODR is comprehensible, digestible, and accessible. As such, it's <em>actually</em> an effective learning tool. Shocking! 

Anyhow, the crux of this post is -- in addition to praise for Metz' work -- the Ruby `Struct` class. I came across this neat little 'class helper', if you will, for the first time in Chapter 2 of POODR.

<br>

<h3>What is a Struct?</h3>

According to the official Ruby documentation, a <a href="http://ruby-doc.org/core/classes/Struct.html">Struct</a> is "a convenient way to bundle a number of attributes together, using accessor methods, without having to write an explicit class." After playing around with it a bit in pry, it feels like a quick and cheap way to create `Class`-like instances on the fly that can possess both behaviors and qualities (much like regular `Class`es). Here's a sample `Struct` that I'll build out called `Person`:

```ruby

Person = Struct.new(:name, :age, :gender) do

  def greet_world
    "Hello world, my name is #{name}."
  end

  def ask_question
    "What is your favorite programming language?"
  end

end


stephanie = Person.new("Stephanie", "26", "female")

stephanie.name          # => "Stephanie" 
stephanie.age           # => "26"
stephanie.gender        # => "female"

stephanie.greet_world   # => "Hello world, my name is Stephanie."
stephanie.ask_question  # => "What is your favorite programming language?"

```

Cool, right? Remember, the symbols you pass to your new `Struct` upon initialization -- in this case `:name`, `:age`, and `:gender` -- act like regular `attr_accessor`s. So I could make some alterations after the matter, like so:

```ruby

stephanie.name = "Ruby"
stephanie.age = "21"

stephanie.greet_world   # => "Hello world, my name is Ruby."

```

...but that might be a little confusing. 

I can now also make a bunch of new `Person`s, instantiating each one with his or her name/age/gender, and he or she will also respond to the `greet_world` and `ask_question` methods.  

<br>

<h3>When would you use a Struct?</h3>

This is a great question. It wasn't immediately clear to my why or when one would use a `Struct`, especially when the more ubiquitous `Class` is always an option. According to what I've read so far in POODR, it seems that using a `Struct` is one way to separate structure from meaning; it plays nicely with `Class`es, and also helps to make your methods more transparent. 

If all of that sounded a bit vague and not yet super helpful, then it might help to look at another example wherein a `Struct` is used within a `Class` in order to break down method responsibilities and also make those methods more transparent:

```ruby

data = [["Stephanie", "female"], ["Matz", "male"], ["Sandi", "female"], ["David", "male"], 
["Aaron", "male"]]

class TransparentRoster
  attr_accessor :participants

  def initialize(data)
    @participants = structify(data)
  end

  def sorted_names
    participants.collect { |person| person.name }.sort
  end

  def participant_list
    puts "This year's participants include:"
    sorted_names.each { |name| puts name }
  end

  # here's where we turn the 2D array of data into struct objects

  Person = Struct.new(:name, :gender)

  def structify(data)
    data.collect { |pair| Person.new(pair[0], pair[1]) }
  end

end

```

The TransparentRoster `Class` above takes a parameter called 'data' -- in this case, that data is coming in the form of a 2-dimensional array. It is immediately dealt with upon initialization, calling on a method named `structify(data)` that turns each `[name, gender]` pair from the given array into `Struct` objects that can be further dealt with via the `:participants` attr_accessor, and which respond to both `.name` and `.gender`. 

In taking this approach, we were able to give the TransparentRoster class <em>mostly</em> the illusion of single-class responsibility (i.e technically, the Roster class shouldn't be responsible for, say, initializing new `Person`s; it should deal solely with duties that might sensibly pertain to a Roster like listing names, ordering them, etc). Furthermore, we were able to keep all of its methods small and single-purpose as well. Finally, the handling of raw data was kept limited to one place -- the `structify(data)` method -- so that if the given data were to change from a 2-dimensional array to a different structure, such as a hash, the code to extract the necessary data would only need to be altered in one place. All other method dependencies could remain relatively unharmed. 

I'm curious to see in what other contexts and real-life code bases I might come across `Struct`s. So far, they seem like a great tool for managing single-class responsibility when you're not yet sure how many classes you ought to build or of what magnitude these classes should be for an evolving project. There's a lot left of POODR to read so maybe subsequent chapters will shed further light on this.

<br>

<h4>KEY TAKEAWAYS</h4>
1. POODR is awesome.
2. A `Struct` is a convenient way to bundle together attributes without having to build out or commit to building a whole `Class`.
3. `Struct`s can be included within `Class`es.
4. If done so, a `Struct` can help illuminate the given `Class`'s 'single purpose' by handling the extraneous stuff; this also keeps the `Class`'s methods short and sweet. 



