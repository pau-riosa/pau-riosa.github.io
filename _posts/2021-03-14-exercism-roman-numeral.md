---
layout: post
author: Pau Riosa
title: "Exercism: Roman Numeral"
---

Hey!

Welcome back to another episode of  [exercism.io](https://exercism.io) exercise wherein we practice our logic and problem solving capabilities.

Okay! so I got this new challenge called `Converting a number into a Roman Numeral`.

![figure 1 Exercism: Roman Numeral Challenge](/assets/images/roman-numeral.png)

It says there that it is easy, but as for me it wasn't hahaha!

### Start to Analyze!

As for me, the key hints to solve the problem is by the power of `algorithm` and `pattern matching`! Hooray 🔥

Honestly I struggled a lot on juggling different ideas on how to solve this problem. So first I started to gather some information that
can be useful for me.

### Solution

```elixir 
@doc """
  Convert the number to a roman numeral.
"""
@spec numeral(pos_integer) :: String.t()
def numeral(number) do
end
```

Given the function doc and spec, I started to think that I need to; 

- `convert integer to string`
- `split and turn them into an array`

```elixir
@doc """
  Convert the number to a roman numeral.
"""
@spec numeral(pos_integer) :: String.t()
def numeral(number) do
  numbers =
    number
    |> Integer.to_string()
    |> String.split("", trim: true)
end
```

In this way, I thought I could manipulate them one by one and match the corresponding values according to their place number.
So to satisfy it;

- using `Enum.with_index()` I jump into the data and transform them into arrays elements together with their indexes.

```elixir
@doc """
  Convert the number to a roman numeral.
"""
@spec numeral(pos_integer) :: String.t()
def numeral(number) do
  numbers =
    number
    |> Integer.to_string()
    |> String.split("", trim: true)
    |> Enum.with_index()
end
```

Now the next thing that I did was to `transform the data into a map` because I thought in this was I could pattern match depending on their
index as their place number
```elixir
@doc """
  Convert the number to a roman numeral.
"""
@spec numeral(pos_integer) :: String.t()
def numeral(number) do
  numbers =
    number
    |> Integer.to_string()
    |> String.split("", trim: true)
    |> Enum.with_index()
    |> Enum.map(fn {x, index} ->
    {index, String.to_integer(x)}
    end)
    |> Map.new()
end
```
Finally, I created a private function named `to_numeral/1` that accepts a map.
```elixir
@doc """
  Convert the number to a roman numeral.
"""
@spec numeral(pos_integer) :: String.t()
def numeral(number) do
  numbers =
    number
    |> Integer.to_string()
    |> String.split("", trim: true)
    |> Enum.with_index()
    |> Enum.map(fn {x, index} ->
    {index, String.to_integer(x)}
    end)
    |> Map.new()
    |> to_numeral
end
```


### WTF is `to_numeral/1` been doing? 🤫🤫🤫

So the next plan that I have is to create a new private function that will turn this `Map` into `Roman Numeral` values.
```elixir 
defp to_numeral(%{0 => thousands, 1 => hundreds, 2 => tens, 3 => ones}) do
  parse(thousands, :thousands) <> to_numeral(%{0 => hundreds, 1 => tens, 2 => ones})
end

defp to_numeral(%{0 => hundreds, 1 => tens, 2 => ones}) do
  parse(hundreds, :hundreds) <> to_numeral(%{0 => tens, 1 => ones})
end

defp to_numeral(%{0 => tens, 1 => ones}) do
  parse(tens, :tens) <> to_numeral(%{0 => ones})
end

defp to_numeral(%{0 => ones}) do
  parse(ones, :one)
end
```

Yeah I know! there are so many movings parts here. It kind a hard to admit that I did all of this but life isn't always perfect.
I need to be dumb sometimes for me to learn. So you know how this ends.

I created a private function `parse/2` that turns this numbers according to their  equivalent value in 
roman characters.

So in all, I've created about `90+` line of code just to deliver my answer. For the next blog, my goal is to refactor this one and come up with 
a much better approach and apply it to my future problem solving at exercism: track elixir.

You can check out my solution [here](https://exercism.io/tracks/elixir/exercises/roman-numerals/solutions/a9544a91745e4cbab45758624d52a925)
