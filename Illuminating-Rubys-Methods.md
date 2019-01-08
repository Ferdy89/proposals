# Illuminating Ruby's Methods

## Abstract

Function decorators are an elegant way to add behavior to regular functions
with a clean syntax. Although Ruby doesn't have them, we can build them
ourselves! We're going to navigate our metaprogramming options to change the
language to our taste.

Come to this talk to learn about Ruby's methods, bindings, and how to use
metaprogramming to have them work together. Not only that, you'll find the
inspiration to extend Ruby to write it however you want to look.

## Description

This talk is a dive into some of Ruby's metaprogramming features through the fun
exercise of creating a library to emulate function decorators. It requires some
understanding of functions and their runtime context, although we'll go through
the basic ideas at the beginning. Developers interested in changing the Ruby
language from Ruby itself will learn and have fun with this talk.

Function decorators are a powerful feature of some programming languages like
Python that allows wrapping a method with more behavior. For example, this could
be a way to make a Python function retry on errors and timeout after some time:

```python
@with_timeout(seconds=5)
@with_retry(times=3)
def make_http_call:
  # Code that might fail or take long
```

Although Ruby doesn't have function decorators built-in, it's possible to build
it ourselves.

We will go through the journey of learning about Ruby's `method` method and how
it allows us to obtain a reference to any method and pass it around. Its close
relative `instance_method` does a similar thing but it doesn't have a
`Binding`. A `Proc` has a binding but we can use `instance_exec` to run with a
different one. Combining all of these with the powerful `define_method` method,
we will be ready to create the first version of a function decorator.

To make things prettier, we will leverage the return value of the `def` keyword
to be able to decorate methods by prepending our decorators to a method
definition. On top of that, we can leverage Ruby's parser to do some magic with
line breaks to arrive at a syntax like:

```ruby
with_timeout(seconds: 5) >
with_retry(times: 3) >
def make_http_call
  # Code that might fail or take long
end
```

Finally, we will learn about how this might not be a great idea in terms of
performance. The metaprogramming tools used are very flexible but are also very
hard for Ruby's VM to run. Other techniques like `class_eval` can achieve
production-worthy performance at the cost of being more difficult to work with.

All things considered, it's amazing how flexible Ruby is and the kind of things
we can do to the language itself. Think outside the box and change it yourself!
