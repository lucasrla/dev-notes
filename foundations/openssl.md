---
title: openssl
parent: Foundations
nav_order: 5
---

# openssl

[OpenSSL](https://www.openssl.org) is a dependency for several `brew` formulae, but given that Apple has `LibreSSL` by default on macOS Catalina, let's install `openssl` ourselves:

```sh
# openssl - for Transport Layer Security (TLS)
brew update && brew install openssl
```

A few caveats regarding `openssl`:

> `openssl@1.1`: A CA file has been bootstrapped using certificates from the system keychain. To add additional certificates, place `.pem` files in `/usr/local/etc/openssl@1.1/certs` and run
`/usr/local/opt/openssl@1.1/bin/c_rehash`. `openssl@1.1` is keg-only, which means it was not symlinked into `/usr/local`, because macOS provides LibreSSL.
> 
> If you need to have `openssl@1.1` first in your `PATH` run: `echo 'export PATH="/usr/local/opt/openssl@1.1/bin:$PATH"' >> ~/.zshrc`
> 
> For compilers to find `openssl@1.1` you may need to set:
> ```zsh
>  export LDFLAGS="-L/usr/local/opt/openssl@1.1/lib"
>  export CPPFLAGS="-I/usr/local/opt/openssl@1.1/include"
> ```

If you want to use the `openssl` we have just installed (and not Apple's `LibreSSL`) without adding it to our `PATH`, we must do something like:

```sh
# this is Apple's
which openssl
  /usr/bin/openssl

openssl version
  LibreSSL 2.8.3

# this is ours, installed from brew
/usr/local/opt/openssl@1.1/bin/openssl version
  OpenSSL 1.1.1g  21 Apr 2020
```