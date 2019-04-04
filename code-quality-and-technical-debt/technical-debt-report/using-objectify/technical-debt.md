# 6.4.1.1  Technical Debt

Objectify is identified as the key potential debt considering the Extensibility quality attribute scenario. It is an interface used by teammates to communicate with Google Data Store through Google App Engine \(GAE\). The technical debt of this comes as result of being locked in to the Google App Engine \(Environment\). We have focused on the quality attribute scenario of extensibility which states the ability to adapt the storage platform on data storage options outside of the Google Cloud Datastore. The following pictorial representation illustrates high dependency on objectify for routine database transactions.

![Figure 10.0: Representation of dependency on Objectify](../../../.gitbook/assets/image%20%289%29.png)

  
Currently, the teammates is using Google cloud service but the extensibility scenario focuses on adding support for other cloud service providers. Whereas, objectify is specifically designed for Google Cloud Datastore and tightly coupled with GAE. Based on the architecture design decisions made for using objectify, it is now hard to add a support to other cloud service providers.

