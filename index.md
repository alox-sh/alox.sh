---
title: Get Started
layout: home
nav_order: 1
---

{: .warning-title }
> Disclaimer
>
> This is not a JAFR [^1]

{: .info-title }
> Alox is
>
> A collection of helper functions, decorators and other utilities aiming to *further* ease building (particularly rest API and web) servers with Go's `http` stdlib.

## Install with Go

```bash
go get -u alox.sh
```

## Usage

```go
package main

import (
    "fmt"
    "net/http"

    "alox.sh/server"
)

const addr = ":8080"

func main() {
    api := server.NewAPI(func(api *server.API, responseWriter http.ResponseWriter, request *http.Request) {
        api.MarshalAndWriteJSON(responseWriter, request, map[string]string{
            "method": request.Method,
            "path": request.URL.Path,
        })
    })

    fmt.Printf("Listening on %s\n", addr)
    http.ListenAndServe(addr, appServer)
}
```

## Fork on GitHub

1. Fork the repository on GitHub
    <div class="mt-2"><a class="github-button" href="https://github.com/alox-sh/alox/fork" data-color-scheme="no-preference: light; light: light; dark: dark;" data-icon="octicon-repo-forked" data-size="large" aria-label="Fork alox-sh/alox on GitHub">Fork on GitHub</a></div>
2. In order for you to be able to install your new fork, you'll have to change the package name to reflect the new name. This package is being served under custom domain, but unless you're not too lazy to setup domain and a web server, **your new package name new will likely look something like this: `github.com/<USERNAME>/<FORK_NAME>`**.<br/>To ease this task you can use a prepared script `scripts/rename-package.sh` which takes your new package name as an only argument:
    ```bash
    scripts/rename-package.sh github.com/j.doe/alox-but-better
    ```

----

[^1]: Just Another Fucking Router
