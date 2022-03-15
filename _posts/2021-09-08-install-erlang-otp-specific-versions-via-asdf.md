---
layout: post
author: Pau Riosa
title: Install Erlang OTP 22.x in macOS using asdf package manager
image_path: /assets/images/IMG_20220221_153902.jpg
---

### Specs

1. macOS version 11.5.2
2. xcode version 12.5.1

### export environmental variables in your shell

> As for me I am using `zshrc` file.
> You can also refer to [erlang documentation](http://erlang.org/documentation/doc-9.3/doc/installation_guide/INSTALL.html#id58804) about the different tags used in here.

```
export MACOSX_DEPLOYMENT_TARGET=10.7 # Big Sur breaks all the things with kerl
export KERL_BUILD_DOCS=yes
export KERL_INSTALL_MANPAGES=yes
export wxUSE_MACOSX_VERSION_MIN=11.3
export EGREP=egrep
export CC=clang
export CPP="clang -E"
export KERL_USE_AUTOCONF=0
export KERL_CONFIGURE_OPTIONS="--disable-debug \
                               --disable-hipe \
                               --disable-sctp \
                               --disable-silent-rules \
                               --enable-darwin-64bit \
                               --enable-dynamic-ssl-lib \
                               --disable-parallel-configure \
                               --enable-kernel-poll \
                               --enable-shared-zlib \
                               --enable-smp-support \
                               --enable-threads \
                               --enable-wx \
                              --with-ssl=/usr/local/opt/openssl@1.1 \
                              --with-wx-config=/usr/local/Cellar/wxwidgets/3.1.5/bin/wx-config \
                              --with-javac"

```

### asdf erlang installation for other OTP versions

- install [asdf package](https://github.com/asdf-vm/asdf) manager via homebrew

```
$ brew install asdf
```

- add [erlang plugin](https://github.com/asdf-vm/asdf-erlang)

```
$ asdf plugin add erlang
```

- remove [autoconf](https://www.gnu.org/software/autoconf) using homebrew and manually install **autoconf version 2.69**

```
$ brew remove autoconf
```

```
$ curl -O http://ftp.gnu.org/gnu/autoconf/autoconf-2.69.tar.gz
$ tar zxvf autoconf-2.69.tar.gz
$ cd autoconf-2.69
$ ./configure && make && sudo make install

```

- select an erlang version that you want

```
$ asdf list-all erlang

```

- install erlang

> Because of privileges issues on my laptop, I intended to use `sudo` command. In my case I choose erlang 22.3 to install

```
$ sudo asdf install erlang 22.3
```

> On the other hand, you can also use a simple `asdf` command if you are confident that you have the right privileges in your laptop.

```
$ asdf install erlang 22.3
```

- run `erl -v` command and see to it that you have seen this

![Screen Shot 2021-09-08 at 4.32.30 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1631089993461/8Rs5rB9bH.png)

references: [elixir forum](https://elixirforum.com/t/erlang-otp-24-0-released/39630/29)
