---
layout: writing
title: "Initial commit"
description: "There is always an initial commit. That first step that sets us
             up in our way. This is my initial commit."
---
Ruby Quickstart for Refugees:

--

`#` is a comment.
You don't need semicolons.
Ruby aims to be elegant and readable, so punctuation and boilerplate are
minimal.

--

Ruby is truly object-oriented.  Everything is an object.

`1.to_s      #=> "1"`

--

You don't need parens if the statement is unambiguous:
"hello".gsub 'h', 'H'                 #=> "Hello"

But they are needed if the statement is ambiguous:
"olleh".gsub("h", "H").reverse        #=> "Hello"

--

Classes can be reopened at any time, by anyone with access to the interpreter.

class Fixnum
  def even?
    self % 2 == 0
  end
end

1.even? #=> false

--

Literal Types:

Symbols look like :this_is_a_symbol
There is only one representation of a given symbol in memory, so it really
means "the thing named :this_is_a_symbol" to the ruby interpreter.  In ruby,
we prefer symbols over hardcoded globals or strings. They're very lightweight.

Hashes (much like an associative map) look like
my_hash = {:a_symbol => 3, "a string" => 4}
We reference hashes like
my_hash[:a_symbol] #=> 3

Arrays use the familiar [a, b, c] format.  Arrays are sized dynamically and
can be of mixed types.

a = [1, 2, 3]
a.push 4       #=> [1, 2, 3, 4]
a.pop          #=> 4
a[0]           #=> 1

Strings

We use "string #{ruby code} string" for String interpolation.

def declare_fun(string)
  "I think that #{string} is fun!"
end

declare_fun "ruby" #=> "I think that ruby is fun!"

--

Methods can take blocks, which are like anonymous functions.
[1, 2, 3].each do |item|
  puts "#{item} is #{item.even? ? "even" : "odd"}."
end

This takes each item in the array, assigns it to the variable "item", and
prints whether it's even.

--

Blocks can also return a value.  Map translates each item in an array.

["hello", "world"].map{ |string| string.upcase } #=> ["HELLO", "WORLD"]

--

Ruby uses duck typing, which means we don't care what an object is as long as
it does what we want to do with it.

def print_even_or_odd(array_like_thing)
  array_like_thing.each do |item|
    puts "#{item} is #{item.even? ? "even" : "odd"}."
  end
end

print_even_or_odd [1, 2, 3]
print_even_or_odd 1..3 # a Range object, which also responds to each

--

Advanced topics that are worth discussing if you're interested:

Ruby provides really powerful tools for meta-programming (writing code that
writes code on the fly) and introspection. This is most of the magic of Rails.

Ruby lets you handle undefined method calls at the source with a "catcher"
method called method_missing.  This is the entry point for a lot of powerful
stuff.

Ruby has a mixin-based inheritance system that is somewhat like multiple
inheritance with one primary ancestor class.

Ruby doesn't provide much protection from other programmers.  Private really
just means "please don't come in."  The ruby philosophy is that if someone has
access to your runtime environment, you should make sure they're trusted.
Spend your time writing code, not protecting yourself from other programmers.

Classes are objects, and class methods are really just methods on the class
object.  Code evaluated in the scope of a class definition acts on the class
object.

[poli]: http://www.poligran.edu.co/