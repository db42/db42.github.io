---
layout: post
title: X-HTTP-Method-Override with AFNetworking
---

Here is another short post related to `AFNetworking`.

## What is X-HTTP-Method-Override?
X-HTTP-Method-Override is a HTTP header field which tells the web service to ignore the actual HTTP method and rely on its value instead.
For example:

* Using `X-HTTP-Method-Override: GET` with a `POST` request  
If your query parameters length exceeds the HTTP `GET` path length limit, then do a HTTP `POST` and set the method override as `GET`.
Service will read the `POST` request body and process this as `GET` parameters.   
This requires support from the web service - Rails, by default, supports this.

* `X-HTTP-Method-Override: PUT` with a `POST` request  
Do a HTTP `POST` to bypass your firewall restriction on `PUT` request.

## How to use it with `AFNetworking`

```objective-c
AFHTTPRequestOperationManager *manager = [[AFHTTPRequestOperationManager alloc] initWithBaseURL:[NSURL URLWithString:ROOT_URL]];

[manager.requestSerializer setValue:@"GET" forHTTPHeaderField:@"X-HTTP-Method-Override"];
```

## Further Resources

* [X-HTTP-Method-Override](http://www.endurasoft.com/Blog/post/X-HTTP-Method-Override.aspx)
* [X-HTTP header method override and REST APIs](http://fandry.blogspot.in/2012/03/x-http-header-method-override-and-rest.html)

