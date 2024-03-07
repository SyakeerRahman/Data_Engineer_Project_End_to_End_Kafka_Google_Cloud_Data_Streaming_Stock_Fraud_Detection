# Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection

<img width="575" alt="Screenshot 2024-03-07 163632" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/6fedef00-3b60-468b-ab9c-60481920ff25">

## Prerequisites

1. Create a Confluent Cloud Account.
- Sign up for a Confluent Cloud account here.
- Once we have signed up and logged in, click on the menu icon at the upper right hand corner, click on “Billing & payment”, then enter payment details under “Payment details & contacts”. A screenshot of the billing UI is included below.
``-Note: We will create resources during this workshop that will incur costs. When we sign up for a Confluent Cloud account, we will get free credits to use in Confluent Cloud. This will cover the cost of resources created during the workshop.
``

## Objective
We will learn and explore how to leverage Confluent Cloud, powered by Kora Engine, to build a real-time streaming analytics use case and activate the power of data with Google Cloud services such as BigQuery, AutoML, Looker Studio etc.

During the session, we will explore:

- The common challenges of Apache Kafka Deployments
- How you can easily activate Confluent Cloud on Google Cloud Marketplace
- How to connect Google Cloud Services with Confluent Cloud
- The benefits of Confluent Cloud for production workloads on Google Cloud

## Log into Confluent Cloud

1. Log into Confluent Cloud and enter your email and password.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/f3409f48-57f2-44ce-87a6-6eb5a83b0de2)

## Create an Environment and Cluster

An environment contains clusters and its deployed components such as Apache Flink, Connectors, ksqlDB, and Schema Registry. You have the ability to create different environments based on your company's requirements. For example, you can use environments to separate Development/Testing, Pre-Production, and Production clusters.

1. Click + Add Environment. Specify an Environment Name and Click Create.
``Note: There is a default environment ready in your account upon account creation. You can use this default environment for the purpose of this workshop if you do not wish to create an additional environment.``

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/6a066418-6fe8-4d7d-8482-38b96f6935e0)

2. Select Essentials for Stream Governance Packages, click Begin configuration.

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/2df112ae-c350-4330-8cd0-e6bfb7fb6d0b)

3. Select GCP Sydney Region for Stream Governance Essentials, click Continue.

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/b49e0663-41cd-4e65-b762-6a8186baa670)

4. Now that you have an environment, click Create Cluster.

Note: Confluent Cloud clusters are available in 3 types: Basic, Standard, and Dedicated. Basic is intended for development use cases so you will use that for the workshop. Basic clusters only support single zone availability. Standard and Dedicated clusters are intended for production use and support Multi-zone deployments. If you are interested in learning more about the different types of clusters and their associated features and limits, refer to this documentation.

5. Chose the Basic cluster type.

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/beaf9dd8-a3c8-4d00-a057-ca4de57602ff)

6. Click Begin Configuration.
   
7. Choose GCP as Cloud Provider and your preferred, region, and availability zone accordingly.
   
8. Specify a Cluster Name. For the purpose of this lab, any name will work here.

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/50a08e96-8a45-4cf8-bada-b841c471dbfb)

9. View the associated Configuration & Cost, Usage Limits, and Uptime SLA information before launching.
    
10. Click Launch Cluster.

## Create a ksqlDB Application

1. On the navigation menu, select ksqlDB and click Create Application Myself.

<img width="659" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/1f0277ce-f22c-4165-82e1-c54a0b7e9997">

2. Select Global Access and then Continue.
   
3.Name you ksqlDB application and set the streaming units to 1. Click Launch Application!
``Note: A Confluent Streaming Unit is the unit of pricing for Confluent Cloud ksqlDB. A CSU is an abstract unit that represents the size of your kSQL cluster and scales linearly.``

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/8a165c64-3e34-417f-a224-49434a770bde)

## Creates Topic and Walk Through Cloud Dashboard

1. On the navigation menu, you will see Cluster Overview.
``Note: This section shows Cluster Metrics, such as Throughput and Storage. This page also shows the number of Topics, Partitions, Connectors, and ksqlDB Applications. Below is an example of the metrics dashboard once you have data flowing through Confluent Cloud.``

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/bc3b336e-dba0-4e1f-9e34-9016ea5f772d)

2.  Click on Cluster Settings. This is where you can find your Cluster ID, Bootstrap Server, Cloud Details, Cluster Type, and Capacity Limits.

3. On the same navigation menu, select Topics and click Create Topic.

<img width="922" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/0c6a2ca4-85b1-49e9-8c58-7ff36797ee3d">

4. Enter users_topic as the topic name, 1 as the number of partitions, and then click Create with defaults.

<img width="695" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/59a76393-fd5a-46e7-9d50-f4f79eda42e6">

5. Repeat the previous step and create a second topic name stocks_topic and 1 as the number of partitions.
``Note: Topics have many configurable parameters. A complete list of those configurations for Confluent Cloud can be found here. If you are interested in viewing the default configurations, you can view them in the Topic Summary on the right side.``


7. After topic creation, the Topics UI allows you to monitor production and consumption throughput metrics and the configuration parameters for your topics. When you begin sending messages to Confluent Cloud, you will be able to view those messages and message schemas.

8. Below is a look at the topic, users_topic, but you need to send data to this topic before you see any metrics.

## Create an API Key

1. Click API Keys on the navigation menu.
<img width="920" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/9034bde0-2a5d-4f1a-8fe1-ef175ea1934a">
   
2. Click Create Key in order to create your first API Key. If you have an existing API Key select + Add Key to create another API Key.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/7f8204c2-106e-40e9-87ab-1ead66b3d163)

3. Select Global Access and then click Next.

4. Copy or save your API Key and Secret somewhere. You will need these later on in the lab, you will not be able to view the secret again once you close this dialogue.

5. After creating and saving the API key, you will see this API key in the Confluent Cloud UI in the API Keys section. If you don’t see the API key populate right away, refresh the browser.

<img width="938" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/05669652-e022-43dc-b6a5-7769828ddad0">

## Create Datagen Connectors for Users and Stocks

1. The next step is to produce sample data using the Datagen Source connector. You will create three Datagen Source connectors. One connector will send sample customer data to users_topic topic, the other connector will send sample product data to stocks_topic topic.

First, you will create the connector that will send data to users_topic. From the Confluent Cloud UI, click on the Connectors tab on the navigation menu. Click on the Datagen Source icon.

<img width="934" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/ddd21b9d-a342-4f5b-ae51-f32dd4a49f19">

2. click additional configuration

<img width="446" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/415ccc1b-e189-44a9-8011-27585e0163ca">

3. select user topic and continue

<img width="895" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/c08c6983-f1a1-4e4d-8fe7-d5250aea3387">

4. click on use an existing API key and key in the details

<img width="866" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/4262982d-8a7c-487b-85f0-0beead318cf7">

5. Enter the following configuration details. The remaining fields can be left blank. API key as from the create API keys step
<img width="434" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/56eeeddd-2544-4958-b66f-1f41e9df459d">

<img width="730" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/58789756-e14c-41c6-a648-d19877aab905">

6. Click on Show advanced configurations and complete the necessary fields and click Continue.

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/261ba583-4003-4871-8463-36babd9d1f53)

7. Before launching the connector, you should see something similar to the following. If everything looks similar, select Launch.
   ![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/b32069f2-e222-4132-a94e-0b7158b8265c)

8. after succeed, it will show something like this
<img width="925" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/fb82539a-40f7-4ad3-9a54-5bd55ad5e69b">
   
9. Next, create the second connector that will send data to stocks_topic. Click on + Add Connector and then the datagen Source icon again. (Repeat 1st step but using stocks connector and not user connector)

10. Enter the following configuration details. The remaining fields can be left blank
<img width="442" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/b887fadc-4fcf-4b25-9052-9af1337a53f0">

11. Review the output again and then select Launch.
Note: It may take a few moments for the connectors to launch. Check the status and when both are ready, the status should show running.

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/956bd2d0-9d33-494d-9634-cd7fc28d5279)

``Note: If the connectors fails, there are a few different ways to troubleshoot the error:
Click on the Connector Name. You will see a play and pause button on this page. Click on the play button.
Click on the Connector Name, go to Settings, and re-enter your API key and secret. Double check there are no extra spaces at the beginning or end of the key and secret that you may have accidentally copied and pasted.
If neither of these steps work, try creating another Datagen connector.``

12. You can view the sample data flowing into topics in real time. Navigate to the Topics tab and then click on the users_topic. You can view the production and consumption throughput metrics here.

13. Click on Messages.
You should now be able to see the messages within the UI. You can view the specific messages by clicking the icon.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/2e829f01-3122-4401-ac9f-a24a2d4e3eae)

14. The message details should look something like the following.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/89cea943-2c87-4784-af3d-913da88acc80)

## Create a Stream and a Table

Now that you are producing a continuous stream of data to users_topic and stocks_topic, you will use ksqlDB to understand the data better by performing continuous transformations, masking certain fields, and creating new derived topics with the enriched data.

You will start by creating a stream and table, which will be the foundation for your transformations in the upcoming steps.

A stream provides immutable data. It is append only for new events; existing events cannot be changed. Streams are persistent, durable, and fault tolerant. Events in a stream can be keyed.

A table provides mutable data. New events—rows—can be inserted, and existing rows can be updated and deleted. Like streams, tables are persistent, durable, and fault tolerant. A table behaves much like an RDBMS materialized view because it is being changed automatically as soon as any of its input streams or tables change, rather than letting you directly run insert, update, or delete operations against it.

To learn more about streams and tables, the following resources are recommended:

Streams and Tables in Apache Kafka: A Primer
ksqlDB: Data Definition

1. Navigate back to the ksqlDB tab and click on your application name. This will bring us to the ksqlDB editor.
``Note: You can interact with ksqlDB through the Editor. You can create a stream by using the CREATE STREAM statement and a table using the CREATE TABLE statement.
To write streaming queries against users_topic and stocks_topic, you will need to register the topics with ksqlDB as a stream and/or table.``

2. First, create a Stream by registering the stocks_topic as a stream called stocks_stream.
``CREATE STREAM stocks_stream (
    side varchar, 
    quantity int, 
    symbol varchar, 
    price int, 
    account varchar, 
    userid varchar
) 
WITH (kafka_topic='stocks_topic', value_format='AVRO');``

![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/3813cd3f-1b93-4324-9800-be1d5a736c46)
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/aae45d3c-9f23-4d26-ace4-9af181b2e5f7)

3. Next, go to the Streams tab at the top and click on STOCKS_STREAM. This provides information on the stream, output topic (including replication, partitions, and key and value serialization), and schemas.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/7859d9a4-3e09-4b32-8f82-716c9453a288)

4. Click on Query Stream which will take you back to the Editor. You will see the following query auto-populated in the editor which may be already running by default. If not, click on Run query. To see data already in the topic, you can set the auto.offset.reset=earliest property before clicking Run query.

Optionally, you can navigate to the editor and construct the select statement on your own, which should look like the following.
``SELECT * FROM STOCKS_STREAM EMIT CHANGES;``

5. You should see the following data within your STOCKS_STREAM stream
<img width="887" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/f2ad7a6b-e63d-4cc4-80bd-a14290151986">

6.Click Stop.
7.Next, create a Table by registering the users_topic as a table named users. Copy the following code into the Editor and click Run.
``CREATE TABLE users (
    userid varchar PRIMARY KEY, 
    registertime bigint, 
    gender varchar, 
    regionid varchar
) 
WITH (KAFKA_TOPIC='users_topic', VALUE_FORMAT='AVRO');``

8. Once you have created the USERS table, repeat what you did above with STOCKS_STREAMS and query the USERS table. This time, select the Tables tab and then select the USERS table. You can also set the auto.offset.reset=earliest. Like above, if you prefer to construct the statement on your own, make sure it looks like the following.
``SELECT * FROM USERS EMIT CHANGES;``
You should see the following data in the messages output.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/f100d8cc-b31d-402c-b4d8-106ee0543b32)

9. Note: Note: If the output does not show up immediately, you may have done everything correctly and it just needs a moment. Setting auto.offset.reset=earliest also helps output data faster since the messages are already in the topics.

10. Stop the query by clicking Stop.
 
## Create a Persistent Query

A Persistent Query runs indefinitely as it processes rows of events and writes to a new topic. You can create persistent queries by deriving new streams and new tables from existing streams or tables.

1. Create a Persistent Query named stocks_enriched by left joining the stream (STOCKS_STREAM) and table (USERS). Navigate to the Editor and paste the following command.
``CREATE STREAM stocks_enriched WITH (KAFKA_TOPIC='stocks_enriched') AS
    SELECT users.userid AS userid, 
           regionid, 
           gender, 
           side, 
           quantity, 
           symbol, 
           price, 
           account
    FROM stocks_stream
    LEFT JOIN users
    ON stocks_stream.userid = users.userid
EMIT CHANGES;``
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/4d7faa1d-7b36-4ad7-9b3c-50fe561d5210)

2. Using the Editor, query the new stream. You can either type in a select statement or you can navigate to the stream and select the query button, similar to how you did it in a previous step. You can also choose to set auto.offset.reset=earliest. Your statement should be the following.
``SELECT * FROM STOCKS_ENRICHED EMIT CHANGES;``
The output from the select statement should be similar to the following:
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/d4edae14-7aa1-401a-8617-3d99940bc218)

3. Note: Now that you have a stream of records from the left join of the USERS table and STOCKS_STREAM stream, you can view the relationship between user and trades in real-time.

Next, view the topic created when you created the persistent query with the left join. Navigate to the Topics tab on the left hand menu and then select the topic stocks_enriched.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/31fe021f-f6bb-4469-a5b4-6242d89ea456)

## Aggregate Data

ksqlDB supports several aggregate functions, like COUNT and SUM, and you can use these to build stateful aggregates on streaming data. In this step, you will walk through some key examples on different ways you can aggregate your data.

1. First, aggregate the data by counting buys and sells of stocks. Navigate back to the Editor and paste the following query to create a new table named number_of_times_stock_bought.

``CREATE TABLE number_of_times_stock_bought WITH (KAFKA_TOPIC='number_of_times_stock_bought') AS
    SELECT SYMBOL,
           COUNT(QUANTITY) AS total_times_bought
    FROM STOCKS_STREAM
    WHERE side = 'BUY'
    GROUP BY SYMBOL
EMIT CHANGES;``

2. Next, query this table by going to the Tables tab and selecting the query option or typing it directly into the Editor. You can also choose to set auto.offset.reset=earliest. If you write the statement yourself, make sure it looks like the following.
``SELECT * FROM NUMBER_OF_TIMES_STOCK_BOUGHT EMIT CHANGES; ``
The results should look something like the following.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/f98cb2ad-7fb7-4484-b6ea-ccc628da2990)

3. Next, create a table that calculates the total number of stocks purchased per symbol. You can choose to set auto.offset.reset=earliest.
   ``CREATE TABLE total_stock_purchased WITH (KAFKA_TOPIC='total_stock_purchased') AS
    SELECT symbol,
           SUM(QUANTITY) AS TOTAL_QUANTITY
    FROM STOCKS_ENRICHED
	WHERE SIDE = 'BUY'
    GROUP BY SYMBOL;``
   Running this query should return something that looks similar to the following.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/003240b9-60a7-483e-a39d-48998fb15ba4)

## Windowing Operations and Fraud Detection

You will walk through a few examples on how to use ksqlDB for Windowing, including how to use it for anomaly or fraud detection. ksqlDB enables aggregation operations on streams and tables, as you saw in the previous step, and you have the ability to set time boundaries named windows. A window has a start time and an end time, which you access in your queries by using WINDOWSTART and WINDOWEND. When using Windowing, aggregate functions are applied only to the records that occur within the specified time window. ksqlDB tracks windows per record key.

There are a few different Windowing operations you can use with ksqlDB. You can learn more about them here.

1. In the ksqlDB Editor, paste the following command in order to create a windowed table named stocks_purchased_5min_window_tumbling from the stocks_topic. You can set the size of the window to any duration. Set it to 5 minutes in this example.
``CREATE TABLE stocks_purchased_5min_window_tumbling WITH (KAFKA_TOPIC='stocks_purchased_5min_window_tumbling') AS
    SELECT symbol,
           COUNT(*) AS quantity
    FROM stocks_enriched
    WINDOW TUMBLING (SIZE 5 MINUTES)
    GROUP BY symbol;``

2. Once you have created the windowed table, use the Editor or the Tables tab to query the table. If you construct the statement on your own, make sure it looks like the following.
``SELECT * FROM stocks_purchased_5min_window_tumbling EMIT CHANGES;``
The output should be similar to the following.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/ff915312-bc11-44f8-844f-3ddbaecb01db)

3.Going along with the theme of fraud detection, create a table named accounts_to_monitor with accounts to monitor based on their activity during a given time frame. In the ksqlDB Editor, paste the following statement and run the query.
``CREATE TABLE accounts_to_monitor WITH (KAFKA_TOPIC='accounts_to_monitor') AS
    SELECT ACCOUNT,
           AS_VALUE(ACCOUNT) AS ACCOUNT_NAME,
           COUNT(*) AS quantity,
           TIMESTAMPTOSTRING(WINDOWSTART, 'yyyy-MM-dd HH:mm:ss Z') AS WINDOW_START,
           TIMESTAMPTOSTRING(WINDOWEND, 'yyyy-MM-dd HH:mm:ss Z') AS WINDOW_END
    FROM STOCKS_ENRICHED
    WINDOW TUMBLING (SIZE 5 MINUTES)
    GROUP BY ACCOUNT
    HAVING COUNT(*) > 10;``

4. Once you have created the ACCOUNTS_TO_MONITOR table, use either the Editor or the Tables tab to query the data from the table. If you construct the statement on your own, make sure it looks like the following.
``SELECT * FROM ACCOUNTS_TO_MONITOR EMIT CHANGES;``
The output from this query should look like the following.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/04437616-2c00-4a9a-b1d3-7676292e335e)

## Pull Queries

Building on our Fraud Detection example from the last step, let’s say our fraud service wants to check on high frequency accounts. The fraud service can send a pull query via the ksql API, today we will just mock it with the UI. Then we can monitor the activity for a suspicious account.

1. First we need to add a property to our query. Pull queries only filter by the primary key by default. To filter by other fields, we need to enable table scans. You can add a property under the auto.offset.reset one already included. You will need to set ksql.query.pull.table.scan.enabled to true
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/e8b2b831-0361-4d02-879b-d86777c4726b)

2. Now let’s run our pull query in the Editor to see how our accounts are behaving.
``SELECT * FROM ACCOUNTS_TO_MONITOR
     WHERE QUANTITY > 100;``
   
3. Once we have identified a potential troublemaker, we can create an ephemeral push query to monitor future trades from our STOCKS_ENRICHED stream. This will continue to push trades to the fraud service for further analysis until it is stopped.
``SELECT * FROM STOCKS_ENRICHED 
	WHERE ACCOUNT = 'ABC123'
	EMIT CHANGES;``

## Connect BigQuery sink to Confluent Cloud

The next step is to sink data from Confluent Cloud into BigQuery using the fully-managed BigQuery Sink connector. The connector will send real time data on accounts_to_monitor into BigQuery.

1. First, you will create the connector that will automatically create a BigQuery table and populate that table with the data from the promotions topic within Confluent Cloud. From the Confluent Cloud UI, click on the Connectors tab on the navigation menu and select +Add connector. Search and click on the BigQuery Sink icon.
<img width="812" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/fb7705e4-3b19-43c3-991e-68e1541aa466">

2. Enter the following configuration details. The remaining fields can be left blank.

<img width="473" alt="image" src="https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/77a53bb8-6fd3-4d8c-a05f-7b4813bee9a2">

Topic Selection
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/7feb3462-39cd-4bb4-b1c4-9cb92777fad8)

Authentication
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/2cb660cf-7d83-4352-9b59-f84012312df3)

3. Click on Next.

4. Before launching the connector, you will be brought to the summary page. Once you have reviewed the configs and everything looks good, select Launch.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/452c0840-edcb-4c83-afb7-1da743ba747d)


5. This should return you to the main Connectors landing page. Wait for your newly created connector to change status from Provisioning to Running.

6. Shortly after, please switch over to the BigQuery page within Google Console to show that a table matching the topic name you used when creating the BigQuery connector in Confluent Cloud has been created within the dataset that you have provided. Clicking the table name should open a BigQuery editor for it.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/162ac204-07ff-4730-b462-90e203702b07)

7. Query results in Bigquery.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/7dfe55fe-0b70-4445-9b40-3008b74da91e)

8. Explore data in Looker Studio.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/bdb42da5-5ad4-4463-a05e-1fda45449679)

9. Looker Studio
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/967d1aab-fe60-43d7-a2a6-c26264bd8541)

## Clean Up Resources

Deleting the resources you created during this workshop will prevent you from incurring additional charges.

1. The first item to delete is the ksqlDB application. Select the Delete button under Actions and enter the Application Name to confirm the deletion.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/aa1b3132-3940-4304-b02f-99db34bb2194)

2. Delete the BigQuery sink connector by navigating to Connectors in the navigation panel, clicking your connector name, then clicking the trash can icon in the upper right and entering the connector name to confirm the deletion.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/be2dc4ca-1ff9-47ae-b783-326974f9d191)

3.Next, delete the Datagen Source connectors for users and stocks.

4. Delete the Cluster by going to the Settings tab and then selecting Delete cluster.
![image](https://github.com/SyakeerRahman/Data_Engineer_Project_End_to_End_Kafka_Google_Cloud_Data_Streaming_Stock_Fraud_Detection/assets/105381652/c0c91ae9-2869-4b8e-88b0-2b3723c0979f)
Delete the Environment by expanding right hand menu and going to Environments tab and then clicking on Delete for the associated Environment you would like to delete







