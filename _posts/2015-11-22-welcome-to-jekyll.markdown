---
layout: post
title:  "Functinal Programming"
date:   2015-11-22 11:10:12 +0100
categories: functional clojure javascript context
---
Context Oriented Programming
============================

In functional programming you often strive for making your functions pure.
A pure function is

```javascript
let stats = {
  visits: 0,
  items: [
    { id: 1, name: "Bottle", },
    { id: 2, name: "Chair", },
  ],
};

function incrementVisitsBy(amount) {
  stats.visits += amount;
}
```

to convert this into a pure function we pass in the `stats` that we want to
increment the `visits for`, like so:

```javascript
functional incrementCounterBy(stats, amount) {
  stats.visits += amount;
}
```

Pure functions have many benefits. For one, they are
a lot easier to unit test than non-pure functions.
This is because e.g. they don't require any setup or teardown. In effect they
don't have any "context" in which they are executed.

Take the example above. Here we would have to reset the property `counter` to
zero, between tests. This is because the variable `stats` is part of the functions
implicit context.

Also, pure functions are usually easy to reason about. Everything that changes is done within the
function, and you only have to understand the function to understand what is
going on.

TODO: Rework

When you start to write pure functions, you realize that most of the problems
you are solving are really ARE math problems. Here is and example:

TODO: Example

But enough about the virtues of pure functions. What I really want to talk about
is the negative aspects.

If you have an application with a large number of your pure function you end
up having to pass the `context` around. I define context as the "thing" the
operation is done on. In the example above `stats` is our context.
All operations


Context-Oriented Programming
============================

In `Clojure` the macro `with-bindings` lets us explicitly set the value of
dynamic variables. This means that the context that everything executed inside
the `with-bindings form` has a context determined by the call site.

TODO

This means we don't have to pass the context as an argument to all the functions
that depend on it. One negative aspect of this, is that you loose the "localness"
of data in the function. You have to understand the application flow that lead
to the execution of the function in order understand the behavior.
I personally get a certain feeling of implicitness (read magic) that I also get
doing meta-programming in Ruby, where using `binding` you store a scope for
later use and change the value of `self`.

The problem is that this  

Object Oriented programming is when you mix data and behavior into objects.
