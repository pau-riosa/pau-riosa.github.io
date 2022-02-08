---
layout: post
author: Pau Riosa
title: "OpenSSL (fast_tls) and Elixir"
keywords: "compilation error on mix compile fast_tls"
---


Recently, I've struggled looking for solution on how to handle compilation error for
a package called `fast_tls` in an elixir/phoenix application that I am working on.

Luckily I have found a solution written by `John Hamelink` with a title [OpenSSL and Elixir](https://johnhame.link/posts/using-openssl-with-elixir/).
The blog explains why the error persist and how to fix it.

If you encountered an error that says...

```
 ==> fast_tls (compile)
Compiled src/fast_tls_app.erl
Compiled src/p1_sha.erl
Compiled src/fast_tls_sup.erl
Compiled src/fast_tls.erl
Compiling c_src/fast_tls_drv.c
c_src/fast_tls_drv.c:21:10: fatal error: 'openssl/err.h' file not found
#include <openssl/err.h>^
1 error generated.
ERROR: compile failed while processing /Users/john/Public/fap/api/api-2.1/deps/fast_tls: rebar_abort ==> 
api \* (Mix) Could not compile dependency :fast_tls, "/Users/john/.asdf/installs/elixir/1.2.3/.mix/rebar 
compile skip_deps=true deps_dir="/Users/john/Public/fap/api/api-2.1/_build/dev/lib"" command failed. 
You can recompile this dependency with "mix deps.compile fast_tls", update it with "mix deps.update fast_tls" 
or clean it with "mix deps.clean fast_tls"
```

`fast_tls` is a TLS / SSL OpenSSL-based native driver for Erlang / Elixir that is using OpenSSL. In my case I am using a OpenSSl v1.1.
You can either compile fast_tls via this command

```
env LDFLAGS="-L$(brew --prefix openssl)/lib" CFLAGS="-I$(brew --prefix openssl)/include" mix compile
```

OR you can indicate the version 

```
env LDFLAGS="-L$(brew --prefix openssl@1.1)/lib" CFLAGS="-I$(brew --prefix openssl@1.1)/include" mix compile
```


> Happy Coding!
