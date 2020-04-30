---
layout: post 
title:  "Phoenix and Rails"
date:   2020-04-30
author: Pau Riosa 
description: "My little intake on what I have discovered between Phoenix and Rails"
---

### Disclaimer

this is just my personal opinions and I don't have any intentions to hurt or bring down others. Peace!

### Where I should start?

Few days ago, I had this opportunity to study a brief background of using [Rails](https://rubyonrails.org/) and I am bit nervous on where I should start.
Gladly, I have my mentor on my back and she suddenly send me some video tutorials on how and where I should begin. 

As a fan of [Phoenix Framework](https://www.phoenixframework.org/) , I should say that there is a lot of similarities and differences between them. I don't know what are the other things but
I would like to highlight the most interesting points I have experience using rails and phoenix.

### Commands

When it comes to commands or task, what I have observed is that...

in Rails you can use `rake`
in Phoenix you can use `mix`
for example: Running a newly created migration file

in Rails: 
```
$ rake db:migrate
```

in Phoenix:

```
$ mix ecto.migrate
```

### Packages

packages are helpful when you want to use specific functionalities for your system or mini apps.

in Rails you can use `gem`
in Phoenix you can use `hex`

gems are included in `GemFile` while hex are included in `mix.exs`

in GemFile, you can include your package as:
```
gem 'package-name', '~> version-number'
```
in mix.exs, you can include your package as:

```
def deps do
  [
    # ...
    {:package-name, "~> version-number"}
  ]
end

```
### Syntax

when it comes to syntax, phoenix and rails are quite the same to each other.
example: in declaring a form input

in Rails:
```
<%= form_for @books do |f| %>
  <%= f.input :title %>
  <%= f.input :description %>
  <%= f.button :submit %>
<% end %>
```

in Phoenix:

```
<%= form_for @changeset, @action, fn f -> %>
  <%= text_input f, :title %>
  <%= text_area f,  :description %>
  <%= submit  "Submit" %>
<% end %>
```
as you can see, they have quite similarities right? the only difference is that 
Rails is tied up with Ruby while Phoenix is with Elixir that is why their declaration 
of functions differs. Amazing 🔥

### Controllers

in Rails:

```
class BooksController < ApplicationController
  def index
  end
end
```

in Phoenix:

```
defmodule MyAppWeb.BookController do
  use MyAppWeb, :controller

  def index(conn, params) do
    render(conn, "index.html")
  end
end
```


yeah! similar but different! (whut? haha), 

Rails controller is defined by a `class` followed by the `name of the controller` and `ApplicationController` signifies that is a controller.` index` is a function passes a connection and renders an `index.html.erb` defined in the `views folder`

Phoenix controller is defined by a `defmodule` followed by the `name of the controller`.
`use MyAppWeb, :controller` signifies that it is a controller. `def index(conn, params)` is a function that passes a connection and renders an `index.html.eex` defined in `templates` folder.

### So much to discover isn't it?

As a first timer using Rails, I was amazed on what are the differences and similarities they have. Those small things
that signifies that there are features that you can find on both ends.

I know there so **MANY** things to say and be discovered between these two frameworks but what I believe is that they both have functionalities that you can use according to your needs.

Again, I just want to share what I discovered and learn from this two amazing frameworks. I have nothing against them and all I can say is that they are brilliant ideas came from brilliant minds. 

If you are curious about it, might as well study them and let you're wildest curiosity play in your mind! **HURRAH!**
