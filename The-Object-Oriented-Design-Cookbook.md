# The Object Oriented Design Cookbook

## Abstract

Do you ever feel Object Oriented Design is often glorified, but there aren't
specific guidelines about how to achieve it? I've struggled with that for
years!

This talk is a list of step-by-step recipes to systematically improve the
design of your code. Come and start improving your code today!

## Description

This talk is about practical steps to take in order to make your code more
Object Oriented. It should be particularly useful to beginners and intermediate
developers, especially the ones that strive to learn about Object Oriented
Design.

I love Object Oriented Design. The idea sounds great in my head, it resonates
with the way my brain works. However, sometimes I feel like the advice about
how to achieve such a design is too generic or ambiguous. Throughout my career,
I've struggled to try to apply all the theory to my code. This talk aims to
condense some of the techniques I've developed to write code that's more Object
Oriented. And it's as specific as I can get.

When attempting to improve the design of code, I often find it difficult to
even find where to start. To help with that, we'll leverage the
[Reek](https://github.com/troessner/reek) gem to find smells in your code. Reek
has a [catalog](https://github.com/troessner/reek/tree/master/docs) of smells
with documentation about why they're bad and how to fix them. I'm going to pick
the ones that are more often brought up to my attention as I'm coding, I'll
explain why they are bad smells in the first place, and finally, I'll explain
step by step what to do to fix them in an object-oriented manner.

Without going into too much detail, here are the smells that I'll be focusing
on and why:

* [Too Many
  Statements](https://github.com/troessner/reek/blob/master/docs/Too-Many-Statements.md).
  This smell is telling us our method is too big. A long method can be a
  hideout for compressed complexity without design. We use it to split up large
  methods into private ones that can help us crystallize our ideas better.
* [Data
  Clumps](https://github.com/troessner/reek/blob/master/docs/Data-Clump.md).
  This smell is telling us we're passing the same arguments together
  repeatedly. This might mean there's an implicit relationship between those
  arguments that we're not documenting. We use it to create new objects that
  make those relationships explicit to future readers.
* [Feature
  Envy](https://github.com/troessner/reek/blob/master/docs/Feature-Envy.md) and
  [Utility
  Function](https://github.com/troessner/reek/blob/master/docs/Utility-Function.md).
  These smells are telling us that we've got logic living far from the data
  they're acting upon. Keeping logic close to the data it uses is a nice way of
  making it visible and accessible to others. We use these smells to move the
  code to where it's more encapsulated, often through the creation of small
  private classes.
* [Irresponsible
  Module](https://github.com/troessner/reek/blob/master/docs/Irresponsible-Module.md).
  This smell is telling us we haven't documented a class or module. Attempting
  to define a class is a nice exercise to reflect on what it does and whether
  it makes sense or needs to be split. We use it to give us a moment to think
  about the story we're trying to tell with our objects, and possibly to name
  them better.
* [Repeated
  Conditional](https://github.com/troessner/reek/blob/master/docs/Repeated-Conditional.md).
  This smell is telling us we have the same `if` statement applied repeatedly,
  and there is a chance that there is a logical path that is blended with
  another one. We might be able to extract that logic into a separate object
  that behaves like the original one, keeping the two paths more organized.
  This is called polymorphism, a classic Object Oriented technique that we can
  implement with the also well-known pattern of the Factory Method.

By the end of this talk, you will have a handful of detailed recipes to apply
to your day to day coding in order to strive for a more clear and Object
Oriented code. You might use some of them, all of them, or even come up with
your own methodologies! I'm very confident that, at least, you'll hear some new
ideas that will agitate your mind.
