# JMS Clustered Topic Example

If you have not already done so, [prepare the broker distribution](../../../../README.md#getting-started) before running the example.

To run the example, simply type **mvn verify** from this directory, or **mvn -PnoServer verify** if you want to start and create the broker manually.

This example demonstrates a JMS Topic deployed on two different nodes. The two nodes are configured to form a cluster.

We then create a subscriber on the topic on each node, and we create a producer on only one of the nodes.

We then send some messages via the producer, and we verify that **both** subscribers receive all the sent messages.

A JMS Topic is an example of **publish-subscribe** messaging where all subscribers receive all the messages sent to the topic (assuming they have no message selectors).

This example uses JNDI to lookup the JMS Queue and ConnectionFactory objects. If you prefer not to use JNDI, these could be instantiated directly.

Here's the relevant snippet from the broker configuration, which tells the broker to form a cluster between the two nodes and to load balance the messages between the nodes.

    <cluster-connection name="my-cluster">
       <retry-interval>500</retry-interval>
       <use-duplicate-detection>true</use-duplicate-detection>
       <message-load-balancing>STRICT</message-load-balancing>
       <max-hops>1</max-hops>
       <discovery-group-ref discovery-group-name="my-discovery-group"/>
    </cluster-connection>

For more information on ActiveMQ Artemis load balancing, and clustering in general, please see the clustering section of the user manual.