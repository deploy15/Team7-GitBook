---
description: >-
  Extensibility (The software architecture must be portable to use other storage
  options outside google cloud datastore)
---

# 5.1  Primary Presentation

**Description**

The above component and connector view capture one of our Quality Attribute Scenario \(QAS\) “Extensibility” which states that the application must be portable to use different storage options outside the Google environment. Analyzing the run-time behavior of the storage architecture of Teammates, it is known that they use two different storage options, first, Google Cloud Storage for storing the student profile data with blob data \(images\) and the second, Google Cloud Datastore for general purpose database operations.

![FIGURE 5.0: C&amp;C View](../.gitbook/assets/image%20%2815%29.png)

