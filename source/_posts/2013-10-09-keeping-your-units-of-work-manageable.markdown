---
layout: post
title: "Keeping Your Units of Work Manageable"
date: 2013-10-09 00:33
comments: true
categories: [methods, method delegation, refactoring]
---

The parallels between good (English) writing and good code continue to abound, and one that really stood out to me today was the idea that <strong>methods are like paragraphs</strong>.

Just think about it. 

Any work of writing worth your dime (screenplays and plays don't really count in this example) -- be it an op-ed piece, a serious article, or a novel -- can be broken down into smaller and smaller units until you're staring at individual letters and punctuation marks. Now, a slightly more meaningful unit of work than individual letters and characters is a sentence, and I'd say the next unit up after a sentence is by and large the most meaningful of all: the paragraph. 

Aside from needing to be well-written in general, conceptually, good paragraphs should <strong>adhere to a single topic</strong>. That is the point of a paragraph: to broach, discuss, debate, or refute ONE MAIN IDEA. And if you find yourself babbling about new or irrelevant ideas, it's probably time for -- you guessed it -- a new paragraph. Paragraphs help us compartmentalize our thoughts so we can build upon them in a logical manner; they're kind of like lego pieces that we can eventually stack together to build something cool. Conversely, how could you build anything <em>without</em> these pieces?? I HAVE NO IDEA. How miffed would you be if you had to build a house with one massive brick? Or how pissed have I been when previous writing students submitted "papers" that were comprised of ONE MASSIVE BLOCK OF TEXT? 

Paragraphs make your work -- as both the writer AND the reader -- more manageable. And I think this is such a key concept in writing code, as well. 

Methods, like paragraphs, are units of work. And these units of work need to be kept manageable, so as to make your life as a programmer (and potential reader of other programmers' code) less painful. How are you going to debug effectively if you're staring at one massive block of code? How can you tell where your errors truly begin and end if your entire program depends on ONE GIANT CHAIN OF METHODS?? I don't know.

Even if you're still having a hard time grasping how crucial this idea is, or if you don't know the first thing about writing code, any layperson with a pair of eyes can see the stark differences between the following two examples of code.

<h5>Here's the first version:</h5>

``` ruby
class Jukebox
  attr_accessor :songs
  APPROVED_COMMANDS = [:list, :help, :exit]

  def initialize(songs)
    @songs = songs.collect {|s| Song.new(s)}
    @on = true

    def on?
      @on    
    end

    def help
      puts "Please select help, list, exit, or play."
      self.command_request
    end

    def command(input)
      if APPROVED_COMMANDS.include?(input.strip.downcase.to_sym)
        self.send(input)    
      elsif input.start_with?("play")
        song_request = input.split("play").last.strip
        self.play(song_request)
      else
        puts "Invalid command"
      end
    end

    def call
      while self.on?
        self.help
      end
    end

    def exit
      puts "Goodbye!"
      @on = false
    end

    def command_request   
      self.command(gets.strip)
    end

  end
```

<h5>Here's the second version (of the same program):</h5>

``` ruby
class Jukebox
  attr_accessor :songs

  def initialize(songs)
    @songs = songs.sort
  end

  def call
    puts "Welcome to Pop Jukebox!"
    puts "Enter a command to continue. Type 'help' for a list of commands."
    exit = false
    while exit == false do
      command = gets.strip.downcase

      case command
      when 'help'
        puts "Enter one of the following commands: help, play, list, exit"
        puts "\n"
      when 'list'
        puts self.songs
        puts "\n"
        puts "Type play to proceed"
        puts "\n"
      when 'play'
        puts "Would you like to play by song title or artist?"
        puts "\n"
        song_title_or_artist = gets.strip.downcase
        puts "\n"
        case song_title_or_artist
        when 'song title'
          puts list_song_titles
          puts "Please select a song"
          puts "\n"
          song_choice = gets.strip.downcase
          play_song_choice(song_choice)
        when 'artist'
          puts list_artists
          puts "Please select an artist"
          artist_choice = gets.strip.downcase
          list_artist_songs(artist_choice)
          song_choice = gets.strip.downcase
          play_song_choice(song_choice)
        else
          puts "Enter one of the following commands: help, play, list, exit"
        end
      when 'exit'
        puts "\n"
        puts "Goodbye! Nice to know ya."
        exit = true
      else 
        puts "Say whaaaaaa?"
      end
    end
  end


  def list_artists
    artists = self.songs.collect do |song|
      song.split(" - ")[0]
    end.uniq
  end

  def list_song_titles
    song_titles = self.songs.collect do |song|
      song.split(" - ")[1]
    end.sort
  end

  def play_song_choice(song_choice)
    self.songs.select do |song|
      if song.split(" - ")[1].downcase == song_choice
        puts "Now playing #{song}!"
      end
    end
  end

  def list_artist_songs(artist_choice)
    self.songs.select do |song|
      if song.split(" - ")[0].downcase == artist_choice
       # then just show that artist's song
       puts song.split(" - ")[1]
      end
    end
    puts "Select song"
  end

end
```

I mean, just from a VISUAL standpoint, it doesn't take rocket science to see that one of the two versions seems to be less... verbose. It seems to rely on small, focused methods that each serve a single purpose and are accessed/called upon by other methods, when needed. This is achieved through something called <strong>method delegation</strong>, where methods pass responsibility along from one to the next, initiating different parts of the program swiftly and efficiently.

Of course, the responsibility of the fledgling Rubyist is to focus on 'making it work' first, then worry about 'making it beautiful'. But somehow, I think considering form and function both is a valuable approach as well. Because if you're thinking in small pieces, and you KNOW that writing code in small pieces is a good thing, then you should have no trouble... <em>writing code in small pieces</em>.


<h4>KEY TAKEAWAYS</h4>

1. Methods are like paragraphs -- give them one 'topic sentence', i.e function, at a time
2. A paper written as one big block of text is egregious... and so is code that relies on one unwieldy method
3. Make your methods small and focused -- you can always call them in other methods!
3. Method delegation is your friend 
