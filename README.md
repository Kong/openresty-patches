# OpenResty Patches for Kong

This repository contains patches for OpenResty to be included in Kong
distributions. Kong users building the OpenResty from sources may also
apply these patches to their OpenResty bundle.

## How to Apply Patches Manually?

While Kong, Inc. takes care of pushing these patches to all the Kong
Community Edition (CE) and Kong Enterprise Edition releases (in
different flavors of distribution packages), you might want to [build
Kong from the sources](https://getkong.org/install/source/), that currently
also means to build OpenResty from sources. Before building OpenResty,
you need to apply these patches.

Currently we have patches for following OpenResty releases, though you might
get them applied to other versions:

* `1.13.6.1`
* `1.13.6.2`

Here are the instructions on how to build OpenResty with patches added to
OpenResty version `1.13.6.2`:

```bash
wget https://openresty.org/download/openresty-1.13.6.2.tar.gz
tar zxvf openresty-1.13.6.2.tar.gz
wget https://github.com/Kong/openresty-patches/archive/master.tar.gz
tar zxvf master.tar.gz
cd openresty-1.13.6.2/bundle/
for i in ../../openresty-patches-master/patches/1.13.6.2/*.patch; do patch -p1 < $i; done
```
And the output should contain:

```bash
patching file lua-resty-core-0.1.15/lib/ngx/balancer.lua
patching file lua-resty-core-0.1.15/lib/ngx/balancer.lua
patching file ngx_lua-0.10.13/src/ngx_http_lua_balancer.c
patching file ngx_lua-0.10.13/src/ngx_http_lua_balancer.c
patching file ngx_lua-0.10.13/src/ngx_http_lua_ssl_certby.c
patching file ngx_lua-0.10.13/t/140-ssl-c-api.t
```

Here are the instructions on how to build OpenResty with patches added to
OpenResty version `1.13.6.1`:

```bash
wget https://openresty.org/download/openresty-1.13.6.1.tar.gz
tar zxvf openresty-1.13.6.1.tar.gz
wget https://github.com/Kong/openresty-patches/archive/master.tar.gz
tar zxvf master.tar.gz
cd openresty-1.13.6.1/bundle/
for i in ../../openresty-patches-master/patches/1.13.6.1/*.patch; do patch -p1 < $i; done
```

And the output should contain:

```bash
patching file lua-resty-core-0.1.13/lib/ngx/balancer.lua
patching file lua-resty-core-0.1.13/lib/ngx/balancer.lua
patching file ngx_lua-0.10.11/src/ngx_http_lua_balancer.c
patching file ngx_lua-0.10.11/src/ngx_http_lua_balancer.c
patching file ngx_lua-0.10.11/src/ngx_http_lua_ssl_certby.c
patching file ngx_lua-0.10.11/t/140-ssl-c-api.t
```

After applying patches you can continue following [build Kong from sources documentation](https://getkong.org/install/source/):

```bash
$ ./configure \
    --with-pcre-jit \
    --with-ipv6 \
    --with-http_realip_module \
    --with-http_ssl_module \
    --with-http_stub_status_module \
    --with-http_v2_module
    … 
```

## License

```
Copyright 2018 Kong Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
