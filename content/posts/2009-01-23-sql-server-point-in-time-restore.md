---
title: SQL Server Point-in-Time Restore

date: 2009-01-23T14:01:00+00:00
url: /sql-server-point-in-time-restore/

categories:
  - Tech
tags:
  - tidy

---
<!--kg-card-begin: html-->

One of the multiple hats that I’m currently wearing for a client is that of SQL Server DBA. In this guise, I have recently fielded a couple of email queries from users concerned about the data recovery options available to them, should application data be inadvertently deleted:

> “What kind of database backup and restore mechanism is in place for [application]? If someone deletes any data from [application] front end is it possible to restore it? Generally the way to recover data would be to restore the database from a database backup file, however this would restore all data held in the backup and would overwrite any changes made since the time of the backup.”

and

> “If user A corrupts data entry in some way, and needs to go back to a version X of the database before the corruption, will user B also have to go back to version X and potentially lose any &#8216;good&#8217; they themselves might have added since version X?”

I replied explaining that this is one of the many reasons for choosing SQL Server to provide the database back-end for critical applications, rather than, say, Access (don’t get me started on the prevalence of Access in mission-critical applications, it’s a bit of a bugbear).

If you have your SQL database recovery model set to Full or Bulk-Logged (and if not, why not?) then it is possible to [restore from transaction log backups to a point in time][1]. So, in a data loss scenario like those outlined in the emails above, you would take a backup of the transaction log, and restore a **new copy** of the database to a point in time just before the deletion. The missing data could then be copied from the restored copy across to the live database. Easy.

Even so, just because this functionality exists doesn’t mean you should plan to use it. Flipping back to my system developer persona makes me question why the application allows users to perform non-logged hard deletes? Soft deletes would be far preferable (i.e. setting a “deleted” bit on the relevant rows). Better still are ledgering systems (like the bank statement paradigm), which handle updates and deletions by making a change entry, or entering an offsetting transaction.

<!--kg-card-end: html-->

 [1]: http://www.microsoft.com/technet/prodtechnol/sql/2000/maintain/sqlbackuprest.mspx#ET2AE