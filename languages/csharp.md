## C-sharp

 - [Async](#async)
 - [Crypto](#crypto)
 - [Facebook](#facebook)
 - [Resources](#resources)
 
### Async

 - [Calling Synchronous Methods Asynchronously](http://msdn.microsoft.com/en-us/library/2e08f6yc.aspx)
 - [Making Asynchronous Requests](http://msdn.microsoft.com/en-us/library/86wf6409.aspx)
 - [Make Multiple Web Requests in Parallel by Using Async and Await](http://msdn.microsoft.com/en-us/library/vstudio/hh696703.aspx)
 - [Accessing the Web by Using Async and Await](http://msdn.microsoft.com/en-us/library/vstudio/hh300224.aspx)

### Crypto

 - [Encrypt/decrypt string](http://stackoverflow.com/questions/202011/encrypt-decrypt-string-in-net)

### Facebook

 - [Graph API](https://developers.facebook.com/docs/graph-api/)
 - [Web API](https://developers.facebook.com/docs/reference/javascript/)
 - [Pictures](https://developers.facebook.com/docs/reference/api/using-pictures/)
 - [Friend list](http://stackoverflow.com/questions/16060479/facebook-api-friends-list)
 - [SDK for .NET](http://facebooksdk.net/docs/web/getting-started/)
 - [SDK for .NET requesting permissions](http://facebooksdk.net/docs/web/permissions/)

### Type of generic object with unknown generic parameters

```csharp
Type t = dict.GetType();
bool isDict = t.IsGenericType && t.GetGenericTypeDefinition() == typeof(Dictionary<,>);

Type keyType = t.GetGenericArguments()[0];
Type valueType = t.GetGenericArguments()[1];
```

### Resources

 - [Tests and thoughts on async io vs multithreading (web requests)](http://www.ducons.com/blog/tests-and-thoughts-on-asynchronous-io-vs-multithreading)
