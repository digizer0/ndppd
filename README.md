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
