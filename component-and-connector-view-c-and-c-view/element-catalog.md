---
description: 'Elements and their properties are described below:'
---

# 5.2  Element Catalog

**Client:**

All the interactions with the application are initiated by the client terminals. A client can be any device \(mobile, tablet, desktop or laptop\) making a request to the Teammates application through URL.

**Application Server:**

All kinds of requests from clients are handled by the application server. When database operations are requested by the clients, the storage module of the application server activates.

**Storage Module:**

Whenever database operations are requested, the storage module makes a decision if the requested data operation contains blob and is about student profile database, or if it is a general database operation request. For the former, it activates the objectify sub-module and for the latter, ProfilesDb sub-module is activated.

**ProfilesDb:**

All kinds of student profile data or blob operations are carried out through ProfilesDb component. It acts as a bridge between Google Cloud Storage and the application storage module. The ProfileDB is just one of the many objects defined within Teammate to access the storage module. Others includes, AccountDb, CourseDb, FeedbackQuestionDb e.t.c

**Objectify:**

The general database operations except the operations related to student profile data and blob data are carried out through Objectify. It acts as a bridge between Google Cloud Datastore and the application storage module.

**Google Cloud Storage:**

It is a student profile data storage and also blob storage for storing student images for the Teammates application.

**Google Cloud Datastore:**

This component is a main application data storage for the Teammates. It is an unstructured data store and is not used for storing blob data and student profiles data.

**Variability Guide**

\(Changes by Karan: Changed objectify v6 to v5 and v7 to v6\)

**Application Server -** To allow for extensibility internal storage operations should be independent of external google cloud built-in storage functions. This is an area of future improvement for Teammates.

**Objectify -** Dependency on the Objectify 5 interface puts tight constraints on data storage options and the applications extensibility. Objectify forces Teammates to use the google cloud data store. Objectify 6 lessens these constraints and would allow Teammates to use a number of other storage options. Upgrading is a likely future change.

