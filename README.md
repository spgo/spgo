spgo
====

speed &amp; simple DSL golang framework 

```
// myapp.go
import "spgo"

get "/" {
    "hello world"
}
```

Install the sp tools:

```
go get github.com/spgo/sp
```

And run with:

```
sp run myapp.go
```

View at: http://localhost:4567

# Routes
In spgo, a route is an HTTP method paired with a URL-matching pattern. Each route is associated with a block:

```
get "/" {
  .. show something ..
}

post "/" {
  .. create something ..
}

put "/" {
  .. replace something ..
}

patch "/" {
  .. modify something ..
}

delete "/" {
  .. annihilate something ..
}

options "/" {
  .. appease something ..
}

link "/" {
  .. affiliate something ..
}

unlink "/" {
  .. separate something ..
}
```

Routes are matched in the order they are defined. The first route that matches the request is invoked.

Route patterns may include named parameters, accessible via the params hash:

```
get "/hello/:name" {
    // matches "GET /hello/foo" and "GET /hello/bar"
    // params[:name] is 'foo' or 'bar'
    "Hello #{params[:name]}!"
}
```

You can also access named parameters via block parameters:

```
get "/hello/:name" |n| {
    // matches "GET /hello/foo" and "GET /hello/bar"
    // params[:name] is 'foo' or 'bar'
    // n stores params[:name]
    "Hello #{n}!"
}
```
