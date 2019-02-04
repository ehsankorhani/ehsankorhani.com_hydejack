---
layout: post
title: "ASP.NET MVC Output Caching"
date: 2016-11-16
author: ehsan
excerpt_separator: <!--more-->
---

We can follow every kind of performance tuning tips & tricks on server side code and on the database queries and indexes. But our application can perform better if it doesn\’t need to go through all those logic and have the response ready for the users.

This is partly can be done by utilizing caching mechanism.

#### OutputCache Attribute
the OutputCache attribute exists on System.Web.Mvc namespace and provides a simple and quick way for the developers to set their caching setting on any controller (or entire class if required).

```csharp
public class HomeController: Controller 
{
    [OutputCache(Duration = 300, VaryByParam = "none)]
    public ActionResult Index() 
    {
        return View();
    }
}
```
<!--more-->
Duration is the amount of time in seconds that we want the application to preserve the output (html) of this controller for us.

Therefore, after the first request that someone makes to this controller, whatever output it produces will stay in memory for 5 minutes. The rest of requests will only receive the same result even if the underlying data has been changed during this time.

#### VaryByParam
When set to “none” ASP.NET will create only one cache for the controller.

```csharp
public class HomeController : Controller
{
    [OutputCache(Duration = 300, VaryByParam = "key")]
    public ActionResult Show(string key)
    {
        // some logic ...
        return View(model);
    }
}
```

In the above example, if we had set the VaryByParam to “none”, then no matter what “key” was, all the users would get the result for the first “key” that was queried (for the next 5 minutes).

However, by specifying VarByParam, the ASP.NET will create different versions of cache for any different “key”.

In case we want to specify multiple parameters, we had to something like the following code:

```csharp
public class HomeController : Controller
{
    [OutputCache(Duration = 600, VaryByParam = "key;name")]
    public ActionResult Show(string key, string name, int record)
    {
        // some logic ...
        return View(model);
    }
}
```

And the following code will vary for each and every parameter

```csharp
public class HomeController : Controller
{
    [OutputCache(Duration = 180, VaryByParam = "*")]
    public ActionResult Show(string key, string name, int record)
    {
        // some logic ...
        return View(model);
    }
}
```

in the args list:

```csharp
public class HomeController : Controller
{
    [OutputCache(Duration = 180, VaryByParam = "*")]
    public ActionResult Show(string key, string name, int record)
    {
        // some logic ...
        return View(model);
    }
}
```
