# JMS Auto Closable Example

If you have not already done so, [prepare the broker distribution](../../../../README.md#getting-started) before running the example.

To run the example, simply type **mvn verify** from this directory, or **mvn -PnoServer verify** if you want to start and create the broker manually.

This example shows you how JMS resources such as connections, sessions and consumers in JMS 2 can be automatically closed on error.

In this instance we auto close a connection after a subsequent call to a JMS producer send fails.