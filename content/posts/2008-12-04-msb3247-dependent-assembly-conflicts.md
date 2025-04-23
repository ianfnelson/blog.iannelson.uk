---
title: MSB3247 – Dependent Assembly Conflicts

date: 2008-12-04T21:12:00+00:00
url: /msb3247-dependent-assembly-conflicts/

categories:
  - Tech

---
Earlier today a dev came over to ask me about a compiler warning he was getting when building a .NET solution:

> MSB3247: Found conflicts between different versions of the same dependent assembly.

This is basically telling you that one project or dependency in your solution is referencing one version of an assembly, whilst another project or dependency is trying to reference a different version of the same assembly. Unhelpfully, the message and build output don’t tell you _which_ dependent assembly is causing the problem!

To solve this, I reached for [NDepend][1] and tried to analyze the compiled assemblies. The conflicting assemblies were both excluded from the analysis and a warning message explained that this was a clash between two versions of System.Web.Extensions.dll &#8211; 3.5.0.0 was being referenced by a Telerik UI control, and an earlier version was being used by the developer’s application. This kind of dependency clash is one potential drawback of relying too heavily on third-party controls.

I was going to suggest bringing the application up to date and referencing the newer dll, but a quick squizz at NDepend’s dependency graph revealed that the Telerik assembly wasn’t actually being used by the application at all, and nor were several other referenced components! Deleting the unused references left a slightly leaner, faster-compiling solution with zero build warnings.

 [1]: http://www.ndepend.com