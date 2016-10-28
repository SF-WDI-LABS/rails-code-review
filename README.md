# Code Review

## Sandi Metz's Rules

Sandi Metz is a programmer, speaker, and author of [Practical Object Oriented Design in Ruby](http://www.sandimetz.com/products#product-poodr). In her 2013 Presentation at the Barcelona Ruby Conference she discusses five "rules" or guidelines for writing solid ruby code.

**[Watch it here](https://www.youtube.com/v/npOGOmkxuio?start=470&end=730)** (3 minutes)

#### Keywords
* `PORO` - "Plain Old Ruby Object"
* `iVar` - "instance variable," e.g. `@user`, `@post`
* `POODR` - "Practical Object Oriented Design in Ruby"

#### The Rules
* **0.** (“You should break these rules only if you have a good reason or your pair lets you.”)
* **1.** 5-lines per method
* **2.** 4 method arguments
* **3.** 100-lines per class
* **4.** Only instantiate one object in the controller

> For some discussion of how this works in practice, see [Thoughtbot's developer blog](https://robots.thoughtbot.com/sandi-metz-rules-for-developers)


#### Exercise

Work with your team to identify violations of the above rules in your project code (hint: take a look at one of your resource controllers!)

**Prompt**: Where can we move/hide some of the logic in our controller logic?

* in a private method on the controller?
* in a helper method, shared between the controller and view?
* in an instance method, on a specific resource/class?

## Fat Models / Skinny Controllers
One mantra in the rails community is that "controllers should be skinny" and "models should be fat".

Just because you have "classes" doesn't mean that you're using an "Object Oriented" approach. Models are more than just "data" they should also encapsulate "behavior" and "knowledge" about the world.

**Prompt**: Imagine that your resource (`user`, `post`) is a livining breathing object. Now, revisit your controller and ask yourself the following questions:

* What problem(s) am I solving / what do I need from my data?
* If I had to ask my resource a question, could the resource answer it?
