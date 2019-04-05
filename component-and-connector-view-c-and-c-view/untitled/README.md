# 5.4  Behaviour Documentation

The sequence diagram above exemplifies creating a course being created and being sent to storage on the GAE database. Teammates depends primarily on web applets in order to get the code across as seen in the figure above. However, behind the scenes a number of java classes are called in order to service the web applet. Once a course is added, an instructor account needs to be updated with the correct permissions to be associated with the account. After the instructor permissions, the account is added to a course database. From here the entire database is passed to objectify in order to transform the information into data that can be read by the google app engine which can then be passed to the google datastore. The teammates storage operations are focused on CRUD operation \(create, read, update, delete\). Essentially before the data itself reaches objectify these operations are performed internally to ensure that the correct data is being uploaded to the google data store. In order to maintain consistency, add/delete operations wait until data persists in the google data store before returning. An assumption here is made that enough time has elapsed to “persist”, meaning that the data has propagated through all of the google data stores before returning. Certain errors could arise due to this design decision, and as such is under review as transactional control isn’t foolproof.

![FIGURE 9.0: Behavioural Documentation](../../.gitbook/assets/image%20%286%29.png)



