---
layout: post
author: Pau Riosa
title: "Today I Learned: DateTimeParsing in Elixir using Timex"
---

### Parse "2021-04-01T14:04:30.444023Z" using Elixir

```elixir

 defmodule DateTimeParser do
   def parsing_time(schedule, timezone) do
     time
     |> Timex.parse!("{ISO:Extended}")
     |> Timex.shift(hours: 24)
     |> Timex.Timezone.convert(timezone)
     |> Timex.format!("%a, %b %d at %l:%M %p", :strftime)
   end
 end

 iex > alias DateTimeParser
 iex > scheduled_for = "2021-04-01T14:04:30.444023Z"
 iex > DateTimeParser.parsing_time(scheduled_for, "America/New_York")
 iex > "Fri, Apr 02 at 10:04 AM"



```
