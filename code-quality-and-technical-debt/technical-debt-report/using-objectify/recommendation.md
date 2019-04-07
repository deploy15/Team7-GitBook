# 6.4.1.2  Recommendation

These can be rectified if Teammates would upgrade from objectify version 5, to objectify version 6+. “Objectify v6+ uses the Cloud Datastore API and can be used from anywhere - GAE Standard, GAE Flex, GCE, or outside Google Cloud entirely” \[1\]. This directly addresses the extensibility issues of multiple data storage options within or outside of the Google Cloud Datastore as the new API being used would not rely on the Google App Engine Datastore, but switch to the Cloud Datastore API.

The Teammates development has commented on their own challenges with the Google App Engine as follows: Platform: TEAMMATES is running on Google App Engine cloud platform, which adds the following challenges.

* It is an emerging platform evolving rapidly. We have to keep up.
* It imposes various restrictions on the application, e.g. each request to the app has to be served within 60 seconds.
* It charges us based on usage. We have to optimize usage.

Within Teammates own development comments they state that they have to keep up with the developmental changes of the Google App Engine. However when doing research Google has stated that they are "in the process of replacing this proprietary interface with standards-based \(REST and GRPC\) interfaces to cloud services. This is the new "Google Cloud SDK" which can be used from both outside and inside GAE Standard. This required a rewrite of Objectify, which is v6" \[5\].

Following the link to "[https://github.com/objectify/objectify/wiki/UpgradeVersion5ToVersion6](https://github.com/objectify/objectify/wiki/UpgradeVersion5ToVersion6)" highlights some of the challenges of upgrading from v5 to v6+ for objectify.

When analyzing the codebase of teammates we see that there are some major codebase changes that would have to occur if they intend to keep up with the Google App Engine cloud platform. This would be a massive undertaking however here are some of the technical debts that could be focused on

* "You will need to call ObjectifyService.init\(\), possibly passing in a custom ObjectifyFactory instance. The previous behavior of starting out with a default ObjectifyFactory incurs a connection cost and may fail in environments which require a custom DatastoreService" \[4\].

As evidenced in the ofyhelper.java file snapshot below we see that an instance to the ObjectifyService has already been implemented under the line \(import com.googlecode.ObjectifyService;\)

![Figure 11.0: Representation of dependency on Objectify](../../../.gitbook/assets/image%20%287%29.png)

If we analyze this further we can look into the ObjectifyService code and find the following snapshot. We can see that the ObjectifyService.java file is the holder of the master ObjectifyFactory and provider of the current thread-local Objectify instance.

![Figure 12.0: Representation of dependency on Objectify](../../../.gitbook/assets/image%20%2814%29.png)

As a result the recommendation would be to create a custom ObjectifyFactory instance within the ofyhelper.java file. And then as we see in the image below each instance of the storage classes are registered with the Google App Engine. This practice is limited to version 5 however.

![Figure 13.0: Representation of dependency on Objectify](../../../.gitbook/assets/image%20%286%29.png)

Our recommendation would be to change to the new version of the ObjectifyFactory instances by using the code below. Here we can register each of the classes inside of an ObjectifyFactory instance and then register and pass the ObjectifyFactory in order to be recognized by the new Google Cloud SDK.

![Figure 14.0: Representation of dependency on Objectify](../../../.gitbook/assets/image%20%2811%29.png)

