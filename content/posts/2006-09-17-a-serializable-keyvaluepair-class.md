---
title: A Serializable KeyValuePair Class

date: 2006-09-17T17:09:00+00:00
url: /a-serializable-keyvaluepair-class/

categories:
  - Tech

---
<!--kg-card-begin: html-->

Having accepted that [Returning DataSets from WebServices is the Spawn of Satan and Represents All That Is Truly Evil in the World][1] (or at least, not exactly best practice), I’ve been trying to make a conscious effort to instead use lightweight custom objects in my middle tier, to be exposed via web services for use by other applications. I felt sure that some of the new Generic classes in the .NET 2.0 FCL would help me in my quest. Specifically, as I often need to expose simple arrays of Key/Value Pair metadata, I planned to create an instance of the&nbsp; System.Collections.ObjectModel.Collection class, containing a bunch of System.Collections.Generic.KeyValuePair objects.&nbsp;

Well, this all seemed to go to plan, and worked just fine within my app. But when I exposed the method as a web service, I discovered that neither the Key nor the Value properties were serialized – I was left to consume a lovely generic collection of objects with no members – not a whole lot of use.

A little Googling turned up [this blog entry][2], which explains that the Key and Value properties on the KeyValuePair class are both read-only, and by design the XmlSerializer will not serialize properties that don’t have a set accessor!

Damned if that little matter was going to stop me, I whipped out my copy of Lutz Roeder’s reflector to reverse engineer the KeyValuePair class (to be honest, I could have guessed most of it), and added a <span style="font-style: italic;">private</span> set accessor to both properties, thus persuading the XmlSerializer to, well, do some serializing 🙂

Here’s the code for this new class:



Having done that, to add a little clarity when using this class in the way I anticipate and eliminate repeated code, I decided to create some specific versions of the Collection, ReadOnlyCollection and KeyedCollection classes:



<!>



<!>

<!--kg-card-end: html-->

 [1]: http://www.hanselman.com/blog/ReturningDataSetsFromWebServicesIsTheSpawnOfSatanAndRepresentsAllThatIsTrulyEvilInTheWorld.aspx
 [2]: http://blogs.msdn.com/seshadripv/archive/2005/11/02/488273.aspx