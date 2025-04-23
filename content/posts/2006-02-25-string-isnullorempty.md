---
title: String.IsNullOrEmpty

date: 2006-02-25T14:02:00+00:00
url: /string-isnullorempty/

categories:
  - Tech

---
<!--kg-card-begin: html-->

The single most popular entry on this blog is, surprisingly enough, this [quick post from Summer 2004][1] where I did a quick experiment to "prove" that in .NET the quickest way of proving that a string is empty is to compare its length to zero.

Well, as of .NET 2.0, we have a new static method on the System.String class – `IsNullOrEmpty` – that allows you to easily test whether a string is, well, null or empty!

It’s one of many convenience methods in the .NET 2.0 FCL that tend to get overlooked as developers (perhaps rightly) focus on the big new features such as nullable types, generics, partial classes, etc. I find this method particularly handy when validating parameters passed to publicly-visible methods, as in:

    public void SayHello( string name )  {    if ( string.IsNullOrEmpty( name ) )        throw new ArgumentNullException( "name"; );    Console.WriteLine( string.Concat( "Hello, ", name ) );}

It’s not brain surgery, but it does make the resulting code a little cleaner than in the .NET 1.1 days. Oh, and in case you’re wondering, here’s how the method is implemented in System.String (thanks to [Lutz Roeder’s Reflector][2]):

    public static bool IsNullOrEmpty( string value )  {    if ( value != null )    {        return ( value.Length == 0 );    }    return true;}

More info:

  * [MSDN documentation][3]
  * [FxCop violation documentation][4]

<!--kg-card-end: html-->

 [1]: https://blog.iannelson.uk/is-my-string-empty-some-c-performance-metrics/
 [2]: http://www.aisto.com/roeder/dotnet
 [3]: http://msdn2.microsoft.com/en-us/library/490acw3e%28vs.80%29.aspx
 [4]: http://www.gotdotnet.com/team/fxcop/Docs/Rules/Performance/TestForEmptyStringsUsingStringLength.html