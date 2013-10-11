---
layout: post
title: "Refactoring Using ||="
date: 2013-10-11 10:14
comments: true
categories: [refactoring, or-or-equals]
---

I wanted to write up a short addendum to my previous post, "Ruby: Just Set It. Just Say It" and show you a simple example of refactoring.

What is refactoring, you ask?

In my mind, it's a little like editing your writing. Your first draft might be an incoherent mess, but at least you got your thoughts out. From there, it's your responsibility as a writer to clean up your work so that it best conveys what you mean to say FROM YOUR READERS' PERSPECTIVE. Likewise, refactoring your code is a kind of clean-up process. It shouldn't change your program's external behavior, i.e the final output shouldn't be changing, but HOW your program gets there should have effectively changed. 

I guess this is a little different than editing your writing, in that the former is to better serve the consumer -- the reader; refactoring code, on the other had, doesn't yield any new outcome to the consumer -- the user. However, refactoring does make your code more readable to OTHER CODERS. Which can ultimately mean that future de-bugging efforts will be less painful. That, and you should take pride in your code! Make it as readable, logical, and elegant as possible -- you wouldn't do any differently in your writing, would you??

With that said, here's a side-by-side comparison of my code for the pigeon organizer exercise, pre and post refactoring:

<h4>PRE-REFACTORING, USING 'IF ELSE' LOGIC</h4>

``` ruby

pigeon_list = {}

pigeon_data.each do |property, property_hash|
  property_hash.each do |values, birds_array|
    birds_array.each do |name|
      if pigeon_list[name]                     
        if pigeon_list[name][property]         
          pigeon_list[name][property] << values    
        else
          pigeon_list[name][property] = values     
        end
      else                                         
        pigeon_list[name] = {property => [values]} 
      end
    end
  end
end

```

<h4>POST-REFACTORING, USING THE ||= OPERATOR</h4>

``` ruby

arranged_pigeon_hash = {}

pigeon_data.each do |attribute, value_hash|
  value_hash.each do |traits, names_array|
    names_array.each do |name|
      if arranged_pigeon_hash[name] ||= { attribute => [traits] }
        if arranged_pigeon_hash[name][attribute] ||= traits
          arranged_pigeon_hash[name][attribute] << traits
        end
      end
    end
  end
end

```

The outcome is the same either way, but the refactored version saves me a few lines of code and ultimately captures the logic behind the solution better. 

What the ||= operator does, in a nutshell, is evaluates whatever's on the LEFT side of the operator first. If that condition returns 'true', then the program proceeds to the next line of code, and so on. If the condition is 'false', then whatever's on the RIGHT side of the operator is assigned as the value of the left side. 

Cool, right?!


<h4>KEY TAKEAWAYS</h4>

1. Write code that works first. Then refactor it.
2. Refactoring should't change the final outcome of your program; it should just help your program get there more efficiently, and make your code more readable to OTHER CODERS
3. The ||= ("or or equals") operator is a cool alternative to using 'if else' logic, if you intend for some part of your program to handle new assignment (i.e values to keys, etc.)




