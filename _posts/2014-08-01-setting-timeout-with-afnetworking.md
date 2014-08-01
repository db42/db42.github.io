Chances are you must have experienced the need of setting `timeout` for an HTTP request. Most of the times, this need can be resolved 
by other means. `AFNetworking` has a timeout of `60 seconds`, by default, for all HTTP requests. You must also be very careful in 
choosing whether to modify this default timeout. My advice would be to go through these discussions first:

* [Designing for Real-World Networks](https://developer.apple.com/library/mac/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/WhyNetworkingIsHard/WhyNetworkingIsHard.html)
* [Discussion on AFNetworking](https://github.com/AFNetworking/AFNetworking/issues/1897)

There are genuine use-cases too which require modifying default timeout. For example, doing some operation at app launch time where 
you can live with http request failure but keeping user waiting due to poor network connectivity is not desirable.

```objective-c
AFHTTPRequestOperationManager *manager = [[AFHTTPRequestOperationManager alloc] initWithBaseURL:[NSURL URLWithString:ROOT_URL]];

[manager.requestSerializer setTimeoutInterval:DesiredHTTPRequestTimeout];
```
