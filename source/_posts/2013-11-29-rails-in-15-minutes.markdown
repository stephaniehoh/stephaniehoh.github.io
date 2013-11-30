---
layout: post
title: "Rails in 15 Minutes"
date: 2013-11-29 01:01
comments: true
categories: [rails, ruby on rails]
---

<img src="http://selleo.com/blog/wp-content/uploads/2013/06/Ruby_on_Rails_logo.jpg" height="220" width="150" style="display: block; margin-left: auto; margin-right: auto;">

It's been about 4 weeks since we began learning Rails, and two of those weeks we've spent in manic project mode. Manic in a good way, of course -- as in everyone has been relentlessly devoted to building Rails-based web applications (which has also forced many of us to learn WAY more about AJAX and jQuery on the fly than we ever thought possible in such a short amount of time, especially in tandem with learning an entire framework from the ground up). I think what I'm hinting at is: major brain overload (or brain... overflow? sorry -- terrible joke). 

I take it for granted now that I occasionally have to battle my instance variables when using `form_for`s or forget to set `before_action`s. Because not too long ago, in a very serious way, I literally had <em>no idea what Rails was</em>. 

Sure, I'd heard and read multiple times that Rails "is a framework for building web applications". But what, then, was a framework? How did Ruby fit into it? Were Rails and Ruby on Rails the same thing? I had so many questions prior to these last 4 weeks, and though many had recommended Code School's <a href="http://railsforzombies.org/">Rails for Zombies</a> series, I just couldn't get into it. 

So hopefully, the following breakdown is helpful to anyone who's just embarking upon their soon-to-be awesome journey into Rails:

<br>


<h3>Okay, so what is Rails?</h3>
Rails is a framework for building web applications. 

Just kidding. 

Well, that's actually true, but I'm going to attempt a better explanation because that one is vague and unhelpful. To begin, I'd like to share a few broad (as in, not specific to code or programming) definitions of the word 'framework' that I think best apply to the context of Rails:

<div style="border: solid black 1px; padding: 30px; background: #eee">

  <strong>framework</strong> [ˈfreɪmˌwɜːk]
  <em>n</em>

  <br>
  <br>

  <ol>
    <li>A skeletal structure designed to support or enclose something else</li>
    <li>A set of concepts, assumptions, values, and practices that constitutes a way of viewing reality</li>
  </ol>

</div>

<br>

Okay, now keep those definitions on a mental back-burner. Because they apply to Rails in the sense that they help add brushstrokes and color to the overall picture, but neither of those definitions alone is entirely helpful in grasping -- at the most basic level -- what Rails IS. 

As simply and literally put as possible, Rails is a kind of software, or 'magic kit', that you download locally on your computer via one simple command in your terminal (assuming you already have the RubyGems packaging system): `gem install rails`. Once you've installed it, Rails provides you with a whole bunch of functionality so that you can efficiently start building web applications. In other words, there's a vast library behind the scenes (i.e the Rails source code) into which a lot of complex methods and logic have been defined and pre-coded by some really smart people (like <a href="http://david.heinemeierhansson.com/">this guy</a>) so that you don't have to; instead, you can type some simple commands like `rails new [project name]` or `rails generate scaffold [model]`, and Rails will respond to them. 

<br>

<h3>Now, how exactly is Rails like a 'framework'?</h3>

To relate this back to the above definitions, rails is a framework in the sense that its many built-in shortcuts will magically create skeletal structures (organized directories, basic routes, empty models with their corresponding migrations, etc.) for you to fill in with further details, i.e code and logic. It also encapsulates its creator(s)' values, assumptions, and opinions on programming best-practices, i.e THEIR way of viewing 'reality'.

One of the most definitive illustrations of how 'framework-like' Rails is is the directory structure you instantly get after running `rails new [project name]`. Something like 30 directories come pre-organized, nested and labeled for you -- and some even contain files with pre-written CODE! Thus, rather than leave it up to each individual programmer to organize his or her directories in whatever way he/she deemed fit, the masterminds behind Rails decided to take choice out of the equation and hammer home instead a pre-determined layout to encourage convention. Their values and assumptions are clearly at play here. And though it may sound stiff and undemocratic at first, once you use Rails to build stuff (and conversely, have to jump into other people's Rails projects -- oftentimes to debug), you'll realize how time-saving and mental energy-saving these baked-in conventions truly are. So thank you, DHH, for having an opinion! 

<br>

<h3>So you can build real web apps in fewer than 5 lines of code??</h3>

Well, sort of. Five lines of code will get you some basic CRUD functionality, but that's about it.

Unfortunately, while Rails' out-of-the-box mileage is great, it isn't really going to cut it when you have to build anything for real. That is, any serious web application you build using Rails is going to require a lot of customization, i.e you're going to need to read quite a bit of <a href="http://guides.rubyonrails.org/getting_started.html">Rails documentation</a> and learn how it's really used -- and knowing the Ruby language will really help here.  

A lot of well-known sites and applications do use Rails, including some you may have heard of: Shopify, Twitter, Github, and more. 

Exicted to start Rails-ing, much? 

(If the answer is 'YES!', then I suggest starting <a href="http://ruby.railstutorial.org/ruby-on-rails-tutorial-book#top">here</a>, with Michael Hartl's free Rails tutorial. It's super step-by-step, controlled, and well-explained every step of the way. He also ties in some Git and Heroku, which is a nice touch because it helps contextualize all the other stuff you'll actually come in contact with when you use Rails for real. And personally, I say skip the Rails guide for now until you've had some practice going through the motions, <em>a la</em> Hartl's tutorial. Otherwise, you'll have no context. Besides, guides are best used in general for "sandboxed queries" -- once you have an idea of something specific you need an answer to).

<br>

<h3>Are 'Rails' and 'Ruby on Rails' the same thing?</h3>
Yes.

Rails is simply the shorthand version of saying it; Ruby on Rails is the same thing.

<br>

<h3>How does Ruby fit into it?</h3>

Rails/Ruby on Rails was built using the Ruby programming language, and thus also runs on Ruby. That's a pretty direct way in which Ruby 'fits into the picture'. And as mentioned above, any customization and/or granular manipulation of your Rails-based web application is going to require some real knowledge of Ruby; you don't need to be an expert, but much of what you want to accomplish and much of the control over what data you choose to display (or not display) is going to rely on basic Ruby stuff like the `.each` method, `if else` logic, etc. 

(If you want recommendations on free beginner Ruby resources, I personally like <a href="http://codecademy.com/tracks/ruby">Codecademy</a>, <a href="http://rubymonk.com/">RubyMonk</a>, and Chris Pine's <a href="http://pine.fm/LearnToProgram/">Learn to Program</a>.)

<br>

I think that was approximately 15 minutes' worth of reading? 

Happy Rails-ing! 

