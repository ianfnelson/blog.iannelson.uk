---
title: On 64-bit TFS, Virtualization, and Conchango SCRUM
date: 2009-01-23T12:01:00+00:00
url: /on-64-bit-tfs-virtualization-and-conchango-scrum/
categories:
  - Tech
tags:
  - TFS

---

Earlier this week I picked up a hire car and headed over to deepest Cheshire to install an instance of Team Foundation Server 2008 for a client. Before setting off, I tried to make sure that all the prerequisites were in place – i.e. that there was a suitably-specced server available for use, which was connected to the domain, that all the necessary service accounts were created, and firewall ports opened, etc.

So, I kicked myself somewhat on arrival when I realised that the server was running a 64-bit OS, and remembered that the application tier of TFS only supports 32-bit. Doh! This blog entry is partly intended to prevent me from ever forgetting that again.

However, it all turned out fine in the end. There were other reasons why I didn’t relish the prospect of installing TFS on the box in question – namely that it was also being used as a domain controller and SQL Server (this isn’t as bad as it sounds – the server exists solely to provide an R&D development environment for a new project with demanding timescales). So, the solution I opted for was to install [Virtual Server 2005 R2][1], and then install TFS on a virtual machine running a 32-bit OS. This worked well, as the host server was massively over-specced for the tasks at hand.

I think virtualization is a technology whose time has really come, it certainly makes it very easy to set up development environments like this one, where the number of servers required exceeds the number of physical servers available. Occasionally I come across posts on the web from people who’re trying to install, say, TFS, SQL Server, SharePoint, and Exchange all on the same server, and getting into a pickle. Don’t do it. Embrace virtualization. Developers know all about [separation of concerns][2] when designing software solutions – try the equivalent approach when configuring your development servers.

As an aside – the team chose to use [Conchango’s SCRUM for Team System process template][3], which seems to work very well, and I recommend it for anyone running a project using the SCRUM methodology. Remember, TFS is process-agnostic, you’re not limited to using MSF.

 [1]: http://www.microsoft.com/windowsserversystem/virtualserver/
 [2]: http://en.wikipedia.org/wiki/Separation_of_concerns
 [3]: http://scrumforteamsystem.com/en/default.aspx