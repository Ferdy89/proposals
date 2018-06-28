# Finding the Objects in your Logic

## Abstract

SOLID, Service Objects, Functional style, TDD... Have you ever found yourself
debating about how to design code while a feature is waiting to be shipped?
Seems like you need a system to make design decisions and stay productive!

Metrics are not sufficient, but they're necessary to drive objective
conversations. In this talk you will learn how to analyze the relationship
between data and behavior in your business logic to drive a systematic approach
to create new objects and refactor. This will help you be more in sync with
your team about what direction you want your codebase to follow.

## Description

Object oriented design is a very controversial topic. You probably have formed
an opinion of what constitutes good design and which practices promote
maintainability. The people you work with probably have some ideas on their own
and you know how important is it to stay aligned as a team to have consistent
progress towards a common goal.

Constant communication with your team is always necessary and in this talk you
will learn how to make decisions about your design that you can communicate
effectively. You will learn how to integrate static analysis tools (flog, reek,
rubocop, brakeman) and configure them to the taste of your team to reduce the
uncertainty of whether or not your code lives to your team’s standards.

You will see how after the automated tools have done their part, there might
still be a void of higher level design decisions that are hard to articulate.
You can still analyze the patterns of the data in your code to model objects
and you will learn how proper naming is key to allow objects to emerge from
those patterns. You will end up convinced of how the Factory pattern is a very
powerful tool to enable polymorphism and you can apply it in a systematic way.
This will allow you to understand your logic from a higher perspective and
focus on how to keep encapsulating it properly.

Refactoring is often another controversial topic. You might have found yourself
in the past debating about whether a big design decision is an improvement or
instead a risky rearrangement of code hard to justify. In this talk, you will
learn how to drive your design decisions based on previous advice of the
community in a way that you can become more concise in your arguments. Knowing
what constitutes a code smell and the recipes for their refactors can help your
team become more specific about how to evolve your codebase.

## Pitch

This talk can be very interesting for developers that struggle debating over
design decisions with their teams more often than they think it’s productive.
It can also be very beneficial for developers that want to improve their design
skills and need guidance on actionable points for how to do so.

I used to lead a development team of people with very diverse skills. For some
time I struggled finding ways to effectively make collective decisions with
some team members and also to provide specific guidance to others. I have found
that opinions are hard to communicate without tangible metrics and rules to
back them up. After finding those metrics and defining some rules, the team was
able to be better aligned on a set of collective goals for code quality and
move faster.
