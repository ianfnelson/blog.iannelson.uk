---
title: Database Design – Still Important In These ORM-Obsessed Days

date: 2008-07-29T16:07:00+00:00
url: /database-design-still-important-in-these-orm-obsessed-days/

categories:
  - Tech
tags:
  - tidy

---
[Tobin blogged earlier this week][1] about how quality ORM tools like NHibernate make it easier to code to normalized schemas.

Here&#8217;s a corollary for you: The use of ORM tools doesn&#8217;t absolve the need to maintain good database design principles, and even NHibernate won&#8217;t save you from your own stupidity.

Following an application upgrade release last night, I&#8217;ve spent a disproportionate amount of today trying to debug the following exception, which appeared to originate in an area of the codebase which I personally had heavily modified:

_NHibernate.HibernateException: More than one row with the given identifier was found: 42806, for class: Cmec.Core.Domain.Customer  
at NHibernate.Loader.Entity.AbstractEntityLoader.Load(ISessionImplementor session, Object id, Object optionalObject, Object optionalId)  
at NHibernate.Loader.Entity.AbstractEntityLoader.Load(Object id, Object optionalObject, ISessionImplementor session)  
at NHibernate.Persister.Entity.AbstractEntityPersister.Load(Object id, Object optionalObject, LockMode lockMode, ISessionImplementor session)  
at NHibernate.Impl.SessionImpl.DoLoad(Type theClass, Object id, Object optionalObject, LockMode lockMode, Boolean checkDeleted)  
at NHibernate.Impl.SessionImpl.DoLoadByClass(Type clazz, Object id, Boolean checkDeleted, Boolean allowProxyCreation)  
at NHibernate.Impl.SessionImpl.InternalLoad(Type clazz, Object id, Boolean eager, Boolean isNullable)  
at NHibernate.Type.EntityType.ResolveIdentifier(Object id, ISessionImplementor session, Object owner)  
at NHibernate.Impl.SessionImpl.InitializeEntity(Object obj)  
at NHibernate.Loader.Loader.InitializeEntitiesAndCollections(IList hydratedObjects, Object resultSetId, ISessionImplementor session)  
at NHibernate.Loader.Loader.DoQuery(ISessionImplementor session, QueryParameters queryParameters, Boolean returnProxies)  
at NHibernate.Loader.Loader.DoQueryAndInitializeNonLazyCollections(ISessionImplementor session, QueryParameters queryParameters, Boolean returnProxies)  
at NHibernate.Loader.Loader.DoList(ISessionImplementor session, QueryParameters queryParameters)  
at NHibernate.Loader.Loader.List(ISessionImplementor session, QueryParameters queryParameters, ISet querySpaces, IType[] resultTypes)  
at NHibernate.Hql.Classic.QueryTranslator.List(ISessionImplementor session, QueryParameters queryParameters)  
at NHibernate.Impl.SessionImpl.Find(String query, QueryParameters parameters, IList results)  
at NHibernate.Impl.SessionImpl.Find\[T\](String query, QueryParameters parameters)  
at NHibernate.Impl.QueryImpl.List\[T\]()  
at Ventura.NHibernate.Data.DaoBase\`2.GetByHql(String hql, String[] _params)  
at Cmec.Data.CorrespondenceRequestDao.GetCorrespondenceExtractRequests()  
at Cmec.Core.Tasks.CorrespondenceExtractCreationTask.TaskProcess()  
at Cmec.Core.Tasks.BaseTask.PerformTask()  
at CmecService.CmecService.\_timer\_Tick(Object state)_

Got that?  NHibernate is telling me that it has found two customers on the database with the same surrogate primary key, which is obviously not the case.

Trusting NHibernate as I do, and not generally being the kind of coder who assumes that the technology is to blame, I then spent literally hours digging through my amended code, trying to figure out what nonsense I could be trying to pull that was confusing NHibernate so, but found nothing.

Too late in the day, I dusted down Occam&#8217;s trusty razor, and realised that whilst the main Customers table was correctly enforcing primary keys, I hadn&#8217;t checked the various child tables. Lo and behold, less than a minute later I found the following reference data in an innocuous looking table of referrers:<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blog.iannelson.uk/wp-content/uploads/2023/08/pkviolation.png" class="kg-image" alt loading="lazy" /> </figure> 

Removing the duplicated entry for &#8220;Other&#8221;, which was incorrectly using the same ID as &#8220;Website&#8221;, solved my problems instantly. And needless to say, I&#8217;ve made a note to go add a primary key to that table at the earliest opportunity.

The moral of this cautionary tale &#8211; using an ORM makes your life as an application developer easier, makes it faster to develop a DAL, and (to a large extent) decouples your application from your choice of database. What it doesn&#8217;t do is allow you to forget the tenets of good database design, in fact as Tobin points out it actually serves to encourage them.

 [1]: http://www.tobinharris.com/2008/7/28/is-or-m-is-encouraging-db-normalization