---
layout: post
title: "Ruby: Just Set It. Just Say It."
date: 2013-10-10 1:57
comments: true
categories: [ruby, setting variables, implicit returns]
---

When we're fluent in a language, we take for granted everything about it that feels intuitive. Ever feel that way when asked something specific about English? Say you had to conjure up some intelligent explanation for why certain verbs conjugate irregularly while others don't. You'd probably say something like, "I don't know! I just know that they do. I've always known. If you know English, it's like... intuitive."

You just know. 

Well, until you decide to pick up a foreign language and start the language-learning process from scratch, you have no idea now valuable and hard-earned this intuition is. To have a SENSE of how a language works, how you can play by its rules but still bend it to your will and imagination... this is what fluency feels like. And it feels awesome, because you can really express yourself. 

The alternative, of course, can feel really really frustrating -- and this has been a prevalent feeling so far in my quest to learn to 'speak' Ruby. Everything feels unnatural. I find myself writing most of my code out in the form of pseudo-code, wishfully hoping all the steps I've typed out in plain English will magically transform themselves into Ruby. Come on, you mean the computer CAN'T interpret that? WHY THE HELL NOT.

Anyway. Rather than throw a tantrum (and believe me, sometimes nothing sounds better than a good tantrum), I suppose it'd be more productive for me to share a few Ruby intuition-isms (?) that I've finally picked up on these last few days.


<h3>HOW DO YOU DEAL WITH `.collect`?!</h3>

By this, I don't mean how do you USE `.collect`, per se. Just to be clear though, `.collect` iterates over a data-structure (array or hash) and then, based on what else you've told it to do in your code block, it returns a newly-generated array of all the affected, `.collect`ed items. Cool. What used to really puzzle me, however, was how the hell you further accessed and/or passed around the fruits of this `.collect`ed array's labors. For example, look at this (admittedly wonky-looking) method that uses `.collect': 


``` ruby

# ===== Apple-picker using '.collect' ====== #

def apple_picker(array)
  array.collect do |fruit|
    fruit if fruit == "apple"
  end.compact
end

```

See how I tacked on a `.compact` LITERALLY on the end of the 'end'? I know -- IT LOOKS SO WEIRD. But the real point is, it looks like it's over once I wrap up my 'do' and 'end'. Kaput. No more access to whatever that entire block of code just returned. WHAT IF I WANTED TO DO MORE? Like, how can I make the `.collect`'s return value a THING? Oh, #NBD. Avi finally drilled home for me today this concept: thats_what_variables_are_for = "storing and pointing to things!" So look. If I wanted to store the fruits of `.collect`'s labor somewhere, I literally JUST SET THE WHOLE BLOCK AS = TO A VARIABLE. Like so:


``` ruby

# ===== Apple-picker using '.collect' ====== #

def apple_picker(array)
  some_variable = array.collect do |fruit|     # <-- LOOK! I JUST SET THE 'EQUAL TO' BIT RIGHT HERE
    fruit if fruit == "apple"
  end.compact
end

```

That's it! It's that easy. And now, some_variable effectively 'houses' the result of `.collect`. 

Oh, and by the way -- since `end.compact` looks silly, here the better way to write that using curly braces:


``` ruby

# ===== Apple-picker using '.collect' ====== #

def apple_picker(array)
  array.collect {|fruit| fruit if fruit == "apple"}.compact
end

```
<br>

<h3>HOW DO YOU, LIKE, CHECK IF SOMETHING ALREADY EXISTS?</h3>

This one was a huge epiphany for me. Like HUGE. Of epic proportion. Because NOT knowing this stumped me on basically every problem I had to solve that required 'leveling out' my iteration. Look at this first attempt to organize a hash of pigeons, for example, without explicitly 'leveling out':


``` ruby

pigeon_list = {}
 
pigeon_names = []
pigeon_data.each do |descriptors, details_hash|
  pigeon_names = details_hash.each_value.collect do |name|
    name
  end.flatten.uniq
end
 
pigeon_data.each do |descriptors, details_hash|
  details_hash.each do |qualities, names_array|
    names_array.each do |name|
      if pigeon_names.include?(name)                      # <-- THE ISSUE IS AROUND HERE
        pigeon_list[name] = {descriptors => qualities}
      end
    end
  end
end
 
puts pigeon_list

```

In the above code, my iterator is ultimately only returning the last line of the block that's evaluated, over-writing data with each iteration -- i.e, it keeps re-populating my hash with over-writes, rather than 'leveling out' and catching all the data. The problem, I discovered, was that I NEEDED TO ACCOUNT FOR WHETHER OR NOT SOMETHING ALREADY EXISTS. And how do you do that? YOU JUST STATE IT. Here it is in action below, in the refactored solution:

``` ruby

pigeon_list = {}

pigeon_data.each do |property, property_hash|
  property_hash.each do |values, birds_array|
    birds_array.each do |name|
      if pigeon_list[name]                     # <-- TO CHECK IF IT EXISTS? JUST STATE IT
        if pigeon_list[name][property]         # <-- RIGHT HERE I ASK AGAIN IF SOMETHING EXISTS
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

p pigeon_list

```

See how easy that is? Your instinct, based on English, might be to make up some random 'questions' to ask the entity like `if pigeon_list[name].exists?` or `.already_exists?` -- but THIS IS RUBY. You don't need to ask any questions. YOU LITERALLY JUST STATE THE ENTITY. 

So simple. But mind still blown.


<h4>KEY TAKEAWAYS</h4>
1. Ruby is a pretty English-y language, but it's not ACTUALLY English (so don't expect such)
2. To 'catch' the return value(s) of a `.collect`, simply SET THE ENTIRE BLOCK AS EQUAL TO A VARIABLE (and now it lives in the variable!)
3. To 'level' out your iteration and avoid re-populating with over-writes, you need to check if certain entities (i.e an array) exist already... and how to check? YOU JUST STATE THE ENTITY ITSELF
