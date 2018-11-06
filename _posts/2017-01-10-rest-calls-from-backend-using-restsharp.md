---
layout: post
title: "REST calls from back-end using RestSharp"
date: 2017-01-10
---

There are times you want to make a call to an external REST API (not SOAP web services) from your back-end C# code.

Well, this can be achieved by utilizing HttpClient:

```csharp
HttpClient client = new HttpClient();
```

This is fine. Only you have to take care of the rest of code complexity – especially in the case of an async call. [RestSharp](http://restsharp.org/) library can help you hide all those complexities and focus on your code logic.
<!--more-->
Using this library is very easy. First, just install it from [NuGet](https://www.nuget.org/packages/RestSharp/) package manager or do it via command:

PM> Install-Package RestSharp
Then in you (service layer) code instantiate the REST client as:

```csharp
var client = new RestClient(ApiUrl);
var request = new RestRequest("/api/ControllerName/{id}/{type}", Method.GET);
```

ApiUrl is the service address (e.g. http://example.com)

*{id}* and *{type}* are parameter place holder which we will define later to keep a cleaner code.

```csharp
request.AddHeader("Content-Type", "application/json");
request.AddHeader("Cache-Control", "no-cache");
request.RequestFormat = DataFormat.Json;
request.AddUrlSegment("id", id.ToString());
request.AddUrlSegment("type", type);
```

The above code is just a sample configuration for our GET request.

In case we want to post data, we can write something like that:

```csharp
...
var request = new RestRequest("/api/ControllerName", Method.POST);
...
var body = new
{
    Id = id,
    Type= type
};
request.AddBody(body);
```

And then we execute the request:

```csharp
var response = client.Execute(request);

if (response.StatusCode == HttpStatusCode.OK)
{
    // some logic
}
```

The async call is just very similar:

```csharp
client.ExecuteTaskAsync(request);
```

You can still **Await** the response you get from this async call, or you can call and forget. In the above code, your thread will not be blocked until it receives the response.
