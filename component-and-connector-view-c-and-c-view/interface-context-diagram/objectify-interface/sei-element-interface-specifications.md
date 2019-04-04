# 5.3.2.1  SEI Element Interface Specifications

1.       Interface Identity: CourseDB Interface

2.       Resource Provided:

a.       Resource Syntax: The method is defined named getCourseEntity and takes courseId as a parameter. It returns load\(\).id\(courseId\).now\(\) .

b.       Resource Semantics: The resource performs the functionality of fetching the course details providing the CourseId parameter.

c.       Error Handling: DatastoreTimeoutException, ConcurrentModificationException, or DatastoreFailureException are thrown by Objectify if something goes wrong.

3.       Data Types: The data types of the variables are as follow:

a.       courseId: String

b.       courseName: String

c.       createdAt: DateTime

d.       deletedAt: DateTime

e.       timezone: ZoneId

4.       Error Handling: In case anything goes wrong, the exceptions are thrown. Some of the exceptions that are handled are DateTimeException, EntityDoesNotExistException, InvalidParametersException.

5.       Variability: The interface can be modified to scale up the transactions handling if the peak load is exceeded.

6.       Quality Attributes: The interface can impact the performance while querying the data from the data store when the transactions\(queries\) are performed.

7.       Rationale: The interface is designed to improve the performance of the transactions performed on the data store. It also provides human friendly query interface and easy-to understand transaction model.

8.       Usage Guide: The interface can be used by calling the methods to perform the query. The method call getCourseEntity should return the response with course details if the courseId is passed correctly. Similarly, the other methods \(e.g. updateCourse\) can be called to perform the transactions accordingly.

