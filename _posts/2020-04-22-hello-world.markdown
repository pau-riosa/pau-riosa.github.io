---
layout: post 
title:  "Hello World!"
date:   2020-04-18 22:24:56 +0800
author: Pau Riosa
description: Exercism Elixir Track: Hello World!
---

# Instruction

The classical introductory exercise. Just say "Hello, World!"
```elixir
defmodule HelloWorld do
  @doc """
  Simple returns "Hello, World"!
  """

  @spec hello :: String.t()
  def hello do
    "Hello, World!" 
  end
end
```

Please visit [exercism.io](https://exercism.io/) for exercises! aside from elixir, there 
are lots of programming languages you can try!
