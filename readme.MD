# Spring Boot with Aiven for Apache Cassandra® 

This repo is largely inspired from the the official `spring-guides` GH org, you can find the original [here](https://github.com/spring-guides/gs-accessing-data-cassandra) 

## Setup

### Cassandra

Create a Cassandra service on Aiven, you can either use the console, the CLI or Terraform. 

Once the service is running, use the `Quick Connect` button and connect to your service using `csqlsh`. 

Once connected create the keyspace : 

```
CREATE KEYSPACE aiven_keyspace
        WITH REPLICATION = { 
          'class' : 'SimpleStrategy', 
          'replication_factor' : 2 
      };

```

### Create Truststore

You need to create a Java Trustore based on the CA. Download the CA file from the Aiven console and then run : 

```
keytool -import  \               
  -file ca.pem   \
  -alias CA      \
  -keystore client.truststore.jks

```
You will be prompted to enter a password, choose whatever you want and remember it because you will need it in the `application.properties`. 
Copy `client.truststore.jks` in `src/main/resources`. 

### Update `application.properties`

Open `src/main/resources/application.properties` and replace all the placeholders delimited with `<>`.

## Run the app

You're ready to run the app : `mvn spring-boot:run`



