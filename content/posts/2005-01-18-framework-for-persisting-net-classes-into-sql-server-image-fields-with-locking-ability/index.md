---
title: Framework for Persisting .NET Classes Into SQL Server Image Fields, With Locking Ability
date: 2005-01-18T23:01:00+00:00
url: /framework-for-persisting-net-classes-into-sql-server-image-fields-with-locking-ability/
categories:
  - Tech
tags:
  - .NET

---
There seems to have been a lack of .NET-related stuff on this blog recently, so let me show you something I cobbled together for work purposes last Wednesday:

A common requirement we have in our ASP.NET applications is how to reliably persist object instances for a lengthy period of time. End users shouldn’t have to concern themselves with the concept of Session expiry, and it’s unacceptable for them to return to their PC after nipping off for a coffee to be confronted with the dreaded "Object reference not set to an instance of an object" when they try to continue editing their basket / sales order / timesheet / whatever.

One pattern to solve this, detailed by [Martin Fowler][1] in [Patterns of Enterprise Application Architecture][2], is the **Serialized LOB** (Large Object), which works by serializing the object in question into binary or text which is then stored in a single database field.

An excellent example of how to achieve this using SQL Server and .NET is given by [Peter A Bromberg in this Egghead Cafe article][3].

Building on this example, I’ve put together a generic assembly for persisting and retrieving serializable classes into SQL Server, referenced by a combination of two strings (a username and a key). It is essentially an alternative to storing objects in Session or ViewState. As an additional benefit, it allows you to "lock" objects based on the key, so that only one user can store the same object at a given point in time.

The zip file below includes the source and a SQL script for setting up the required database table and four stored procedures, as well as some unit tests (yes, I am sticking to my New Year’s Resolution!).

The DataStore class contains the various static methods necessary to add, retrieve and delete objects from the store. For example, to save an object you can simply make a call along the lines of:

`DataStore.Add("joebloggs","order1234",objOrder);`

Note that if an object already exists in the store for a given user/key combination, it will be overwritten.

If you additionally want to ensure that no other users have also stored an object with the same name into the store, pass true into the optional fourth parameter:

`DataStore.Add("joebloggs","order1234",objOrder,true);`  

this would throw an ObjectLockedException if any user other than “joebloggs” had previously locked an object called “order1234”.

To retrieve an object, use the Get method. If the object is not found, this will return null. Otherwise, an instance of PersistedObject will be returned – this details information such the datetime at which the object was originally stored and last stored, as well as whether it is locked. The actual object itself is accessible through a "StoredObject" property.

So, to retrieve the sales order object above from the store, a call would be like this:

`SalesOrder objOrder = DataStore.Get("joebloggs","order1234").StoredObject as SalesOrder;`  

That’s pretty much it. There are also methods to retrieve a collection of objects from the store (GetByUser, GetByKey), as well as methods to remove objects from the store (Remove, RemoveByKey, RemoveByUser, Clear).

Feel free to use and cannibalize this code as you see fit. Let me know if you find it useful or interesting, and of course if you have any suggestions for improvements. Oh, and of course it should go without saying that I make no guarantee as to the suitability of this code for any purpose and accept no responsibility for any loss of data etcetera!

---

**Updated 30 October 2005:**

I’ve reworked this code for .NET 2.0, and removed the dependency on the Microsoft Data Access Application Block. Also, the NUnit tests have been replaced with VS2005 unit tests.

**Updated 17 October 2011:**

This project has been [migrated to GitHub][6].

 [1]: http://www.martinfowler.com
 [2]: http://www.amazon.co.uk/exec/obidos/ASIN/0321127420
 [3]: http://www.eggheadcafe.com/articles/20020929.asp
 [6]: https://github.com/ianfnelson/DataStorage