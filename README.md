# NDPPD

***ndppd***, or ***NDP Proxy Daemon***, is a daemon that proxies *neighbor discovery* messages. It listens for *neighbor solicitations* on a
specified interface and responds with *neighbor advertisements* - as described in **RFC 4861** (section 7.2).

## Current status

Version 0.x has been discontinued, and is being replaced by `1.0-devel` which you can find
[here](https://github.com/DanielAdolfsson/ndppd/tree/1.0-devel).

## Changelog for edgerouter

    index 00ca22b..3900339 100644
    --- a/Makefile
    +++ b/Makefile
    @@ -1,11 +1,12 @@
     ifdef DEBUG
     CXXFLAGS ?= -g -DDEBUG
     else
    -CXXFLAGS ?= -O3
    +CXXFLAGS = -O3
    +LDFLAGS  = -static
     endif

    -PREFIX  ?= /usr/local
    -CXX     ?= g++
    +PREFIX  = /ndppd/local
    +CXX     = /usr/bin/mipsel-linux-gnu-g++
     GZIP    ?= /bin/gzip
     MANDIR  ?= ${DESTDIR}${PREFIX}/share/man
     SBINDIR ?= ${DESTDIR}${PREFIX}/sbin

## how to use

1) git clone to your home computer

    `git clone https://github.com/DanielAdolfsson/ndppd.git`

3) run your docker with ndppd directory

    `docker run -v $PWD/ndppd:/ndppd -it --rm ubuntu`

4) update your repository and install g++ of the mips chip(little endian) and make command

```bash
    apt-get update -y
    apt-get install -y g++-mipsel-linux-gnu make
```

5) run make

    `make`

6) move files to your edgerouter

```bash
    scp ndppd xxxx@xxx.xxx.xxx.xxx/ndppd/local/sbin
    scp scripts/ndppd xxxx@xxx.xxx.xxx.xxx/config/scripts/post-config.d
    scp scripts/ndppd.initscript xxxx@xxx.xxx.xxx.xxx/ndppd/local/sbin
```

!!! check owner and execute flags of these files on your edgerouter