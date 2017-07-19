# Code Review

## Sandi Metz's Rules

Sandi Metz is a programmer, speaker, and author of [Practical Object Oriented Design in Ruby](http://www.sandimetz.com/products#product-poodr). In her 2013 Presentation at the Barcelona Ruby Conference she discusses five "rules" or guidelines for writing solid ruby code.

**[Watch it here](https://www.youtube.com/watch?v=npOGOmkxuio&feature=youtu.be&t=7m57s)** (~5 minutes from 7:57-12:23)

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

#### Exercise
Review your code to find a controller action that is "fat".

**Prompt**: Imagine that your resource (`user`, `post`) is a livining breathing object. Now, revisit your controller and ask yourself the following questions:

* What problem(s) am I solving / what do I need from my data?
* If I had to ask my resource a question, could the resource answer it?


#### Rails Code Smells
* Is the majority of your logic in your view? Is it easy to understand and maintain?
* Did you query your model/database *directly* from your view?
* Do you have the same logic repeated across controller actions? e.g. finding a record by id?
* Do you have "magic numbers" in your code -- e.g. a number of value that appears in many places and would be hard to update?
* Did you use view helpers instead of rolling your own html? e.g. Did you use strings (`"/posts/#{id}"`) when you could have used path helpers (`post_path(@post)`)?
* Did you forget to *authorize* users so that anyone who does not own a resource cannot see the `edit` form, or submit to `update` or `destroy`?
* Did you forget to re-render the form when validations fail, thereby wiping the form?
* Did you let the database do the heavy lifting, or did you do most of your looping/sorting/finding in-memory?
* Did you throw everything into a single view, or did you break out cohorent pieces into partials (e.g. index vs. show vs. forms).
* Do you have javascript or css in your html?
* Did you use a 3rd party CDN instead of the asset pipeline?
* Did you add database indexes to fields you query? e.g. if you intend to search by `username` you should index your `username` column.
