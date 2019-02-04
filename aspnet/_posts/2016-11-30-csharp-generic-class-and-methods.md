---
layout: post
title: "C# Generic Class and Methods"
date: 2016-11-30
author: ehsan
excerpt_separator: <!--more-->
---

#### Why Generics?

Suppose that we want to create a method that accepts a class as the parameter and performs some general operations on that. We don\’t know what type of classes will be sent to this method.
<!--more-->
So we have three options:

1. Set concrete class type in method parameters list – but then we have to modify the code and create new methods for every other class which wants to be passed to it.
2. Set abstract or interface type in method parameter list – but then every class must implement that abstract class or interface just for the sake if being able to be passed to this method. That\’s awkward.
3. Set parameter type as Object – well this is better. But hold on, no type-safety feature exist anymore? isn\’t it? casting & boxing/unboxing could be another issue on some occasions as well.

.NET 2.0 offered a 4th option:

4. Generics.

By generics, the type of object will be decided at runtime, so no casting is needed. The code is much cleaner too.

Let’s go with an example:

A method is needed to convert values of an object properties in to a delimited list:

```csharp
public class DelimitedListUtils 
{
    public static string GetDelimitedList(T source, string delimiter) where T: class 
    {
        if (source == null)
            return string.Empty;

        // code to convert properties value into in IEnumerable

        return string.Join(delimiter, propertyValues.ToList());
    }
}
```

**T source**; is the object we are passing in. What is “T”? Well the letter “T” is a convention. You can use anything as long as it matches the
**GetDelimitedList**.

**where T : class**; here I just specify that the parameter we pass in must be of type “class”. But any class will do. You can specify other conditions as well or even omit this part and let the parameter to be of any type.

That’s it.

Now we can use the method in this way:

```csharp
var description = new Description();
var delimitedList = DelimitedListUtils.GetDelimitedList(description, ", ")
```

In case we had multiple generic methods in a class we can move generic declaration to class level.

```csharp
public class DelimitedListUtils where T: class 
{
    public static string GetDelimitedList(T source, string delimiter) 
    {
        if (source == null) return string.Empty; // code to convert properties value into in IEnumerable return string.Join(delimiter,
        propertyValues.ToList());
    }
}
```

Have fun using Generics!
