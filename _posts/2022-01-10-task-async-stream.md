---
layout: post
author: Pau Riosa
title: "Concurrent Data Processing in Elixir TIL Series: Task.async_stream/3"
image_path: /assets/images/IMG_20220221_153902.jpg
keywords: "Concurrent Data Processing, Elixir, Task.async_stream/3, Elixir.Task"
---

## Task.async_stream/3

- returns a `Stream` (Streams in Elixir are data structures that hold one or more operations that don't run immediately, only when explicitly told so) sometimes called `lazy enumerables`
- will start a process and run the function
- works just like `Enum.map/2` and `Task.async/2` combined
- You can set a limit on the number of processes running at the same time via `max_concurrency` option.
- make sure to follow up a call of `Enum` to process the function

## Options

- `max_concurrency` - good for setting the maximum number of task to run at the same time.
- `on_timeout` - When a task reaches a timeout, it will produce an exception, stopping the stream and crashing the current process.
  This is useful for managing one process at a time. You can choose either `exit` or `kill_task`.
- `ordered` is useful if you do not want to idle processes if one task is taking longer.

## Example

```elixir

defmodule MyApp.Sender do
  def send_email(email) do
    ...
  end

  def notify_all(emails) do
    emails
    |> Task.async_stream(&send_email/1, on_timeout: :kill_task, ordered: false, max_concurrency: 1)
    |> Enum.to_list()
  end

  ...
end

iex> Sender.notify_all(emails)
Email to hello@world.com sent.
Email to hola@world.com sent.
Email to nihao@world.com sent.
Email to konnichiwa@world.com sent.
[
  ok: {:ok, "email_sent"},
  ok: {:ok, "email_sent"},
  ok: {:ok, "email_sent"},
  ok: {:ok, "email_sent"}
]

```
