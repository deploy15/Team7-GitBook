# 4.5  Rationale

Teammates is a web-based application product which is entirely hosted on Google App Engine Standard Environment. Google App Engine is a platform as a service offering from Google Cloud Platform. Given this, the entire storage infrastructure of the Teammates is built upon Google Cloud Datastore. In order to perform database operations, Teammates uses Objectify which is a Java data access API for Google Cloud Datastore which is used as an interface between the application storage logic and the underlying datastore. One of the Quality Attribute Scenario of the Teammates is ‘Extensibility’ which states that the application must be flexible to host the database on different platforms outside Google Cloud Datastore and therefore, the storage architecture of Teammates is designed to be adaptable to other data storage options. The migration of the storage system is aimed to be achieved in less than 1 hour.

Teammates design aims for high level of portability to make use of several data storage options outside Google Cloud Datastore. The data storage infrastructure of Teammates is built around 4 core modules:

1.         The **common module** is the facilitator for frequently used utility classes necessary for data structuring in Java, in-app data transfer APIs and exception handling mechanism to prevent run time breakdowns.

2.         Secondly, the **entity module** represents the entire database schema of the Teammates. This module being isolated from rest of the other modules ensures that there is a scope of integrating with other data storage options since the modules that perform the CRUD, search and indexing operations are designed separately.

3.         Third, the CRUD operations on the database are taken care by the **API module** in the Teammates architecture. This module acts as an internal API between the application logic and the underlying datastore. Since objectify is the interface between the storage logic and the google cloud datastore, the API module makes use of ofyhelper classes to use Objectify.

4.         Finally, the **search module** serves as a information search service in the Teammates and it is also designed to be a separate module. The search module also uses API module in order to perform database operations.

The storage architecture of Teammates is aimed to be designed in a flexible manner even if it is entirely dependent on the Objectify for interfacing with the underlying datastore. Although the architecture currently uses Objectify version 5 which only supports interfacing with Google Cloud Datastore, but the Objectify version 6 extends its support to storage services outside google cloud datastore. It provides built-in facilities to help migrate schema changes forward. Objectify also surfaces all native datastore features, including queries, transactions, asynchronous operations, partial indexes and batch operations.

Another important consideration is that the Google Cloud Datastore uses unstructured No-SQL data storage system. This gives rise to the concern of data storage portability into structured databases. Looking at the architecture of the Teammates and the database schema, it is clear that even if the underlying datastore is is unstructured, the schema of Teammates is in a structured form. This makes the architecture more adjustable for migration to other SQL or No-SQL type of databases.

Modifiability is another important Quality Attribute Scenario for the given primary presentation view. While extending Teammates to other data storage options, some modifications in the existing storage architecture become essential. One of the possible modifications would be migrating from Objectify version 5 to version 6. This may not be a tedious process since the modules are strategically isolated from each other and only the API module will be affected.

