---
layout: post
title: "Generic Collections as parameters and return types in C#"
date: 2016-11-27
---

Generic collections provide a convenient way to pass or retrieve data from methods. However, since .NET provides different types of collection, we should know which one to use for any given situation.
<!--more-->
### Interfaces

It is possible and sometimes recommended to use collections interfaces instead of the concrete implementation. This can provide more flexibility in coding.

### Inheritance

*IEnumerable* is the base generic interface in .NET collections. All other collections have implemented this one.

It has only one method: *GetEnumerator()*

This allows the collection to be enumerated.

*ICollection* extends IEnumerable with methods for manipulating data, such as *Add(T)*, *Remove(T)*, *Clear()* and properties like Count.

*IList* and *IDictionary* are both implementing ICollection and extending it with their own properties and methods.

<img class="img-align-right" src="/assets/images/dotnet-collections.gif" alt=".NET Collections" />

IList exposes methods such as IndexOf(T) or RemoveAt(int) to access and manipulate data at specific locations (index) in list. IDictionary<TKey, TValue> also provides methods to alter data using existing “Key”. If the “Key” does not exist the compiler will throw an error. Therefore, the recommended method in such cases is TryGetValue(TKey, TValue).

### Using collection interface as Parameter type

A method can define the accepting parameter type to be of interface type based on what it really needs to do with the collection.

The method defines it’s parameter type as IEnumerable when it only requires enumerating over that collection without altering it.

```csharp
public void Add(IEnumerable collection)
{
    // enumerate using foreach
}
```

The caller can then pass any type of collection to this method since all collections implement an interface which in turn implements IEnumerable (In other words, every collection Is-A ienumerable).

```csharp
var countries = new List
{
    "Australia",
    "USA"
};

Add(countries);
```

### Using collection interface as Return type

A method can return a generic collection interface:

```csharp
public ICollection List(Expression<Func<T, bool>> predicate)
{
    // return collection of T
}
```

The calling code can then cast that returned value to any class that implements that interface.

```csharp
var countries = List(x => x == "Oceania").ToList();
var isAsutraliaInOceania = countries.IndexOf("Australia") > -1;
```
