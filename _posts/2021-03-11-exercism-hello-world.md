---
layout: post
author: Pau Riosa
title: "Exercism: Hello World"
image_path: /assets/images/IMG_20220221_153902.jpg
---

This is the first time that I tried [exercism.io](https://exercism.io) . For me it is a website that trains you on how far can you learn a specific 
programming language. At first I was hesitant but at some point I gave it a shot.

The track that I choose is [Elixir](https://elixir-lang.org/)

Just for a brief background;

> Elixir is a dynamic, functional language for building scalable and maintainable applications.

So if want to give a shot Elixir. That will be cool.

But anyway, The first challenge that I tried is the `Hello World` challenge. So the challenge was

> The classical introductory exercise. Just say "Hello, World!".
> "Hello, World!" is the traditional first program for beginning programming in a new language or environment.
> The objectives are simple:
> Write a function that returns the string "Hello, World!".
>  - Run the test suite and make sure that it succeeds.
>  - Submit your solution and check it at the website.
>  - If everything goes well, you will be ready to fetch your first real exercise.

So what I did was to run this code

```elixir
defmodule HelloWorld do
  @doc """
  Simply returns "Hello, World!"
  """
  @spec hello :: String.t()
  def hello do
    "Hello, World!"
  end
end
```

Yeah, I know nothing much here! It is just a pretty short code that say's `Hello, World!`

For the meantime let me explain to you some parts that we used in order to show `Hello, World!`.

#### defmodule

> `defmodule` is a macro that defines a module with the given `alias` as its name and with contents.
> --- [Elixir](https://hexdocs.pm/elixir/master/Kernel.html#defmodule/2)

`Okay? So what will be it's purpose?`

So just like any other programming languages it defines the `module` that will handle all the necessary `functions`,
`flows` and other stuff for us to create the `Hello, World!`


#### do end

Simply, it is equivalent to the `open/close curly braces` that we can see for example on `C#`, `Javascript`, and `Java` 
that tells us the `scope` of the process.

#### @doc

`@doc` is an attribute that helps developers to define the `meaning` and the `behavior` of the `function`. In our case, 
that is the `hello/1` function that was define using `def`. It accepts `String` values.

#### def

`def` defines a public function with given name and body of the process.

#### @spec

`@spec` is also an attribute that tells developer the `specifications` of the function. Things like;

- What data it will receive?
- What data it will return?


`Okay, so how are we gonna access those modules and functions to show Hello World?`

So assuming you have an `IEx` open
```elixir
> alias HelloWorld
> HelloWorld.hello()
> "Hello, World!"
```

And that's it!

That is how I solve showing the `Hello, World!` 

I know you've got a lot of questions to ask and I know that too!

If you want to have a one on one session feel free to contact me on my email! Just hit `About` 

