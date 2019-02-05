---
layout: post
title: "JavaScript bundling and minification in ASP.NET MVC"
date: 2017-02-14
author: ehsan
excerpt_separator: <!--more-->
---

Continuing on [JavaScript modules: file structure and unification](https://ehsankorhani.com/blog/2017/01/10/JavaScript-file-structure-and-unification) to create a ASP.NET MVC bundle you should follow these steps:

Under “App_Start” folder add a new class and call it: “BundleConfig.cs”. Add a public method “RegisterBundles” to this class.

```csharp
public class BundleConfig
{
    public static void RegisterBundles(BundleCollection bundles)
    {
         // code ...
    }
}
```

<!--more-->
In “Global.asax” file and inside “Application_Start” method insert this code:

```csharp
protected void Application_Start()
{
    // ...
    BundleConfig.RegisterBundles(BundleTable.Bundles);
}
```

Now, your RegisterBundles method is ready.
To create a js file minification follow the following pattern:

```csharp
public class BundleConfig
{
    public static void RegisterBundles(BundleCollection bundles)
    {
        bundles.Add(new ScriptBundle("~/bundles/app").Include(
                    "~/Scripts/Products/product-service.js",
                    "~/Scripts/Products/product-controller.js",
                    "~/Scripts/app.js"));
    }
}
```

Remember to add files in order of the dependency.
ASP.NET supports wild card in adding the files, so you don\’t need to add every single file each time to this list. It also supports adding custom orders, so you define in which order the files to be added to the unified js.

To test the result, set the debug mode to false in “web.config” when you are still in development mode:

```html
<system.web>
  <compilation debug="false" targetFramework="4.6" />;
</system.web>
```
