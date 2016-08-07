---
layout: post
title:  "JDBC Ping Configuration for PostgreSQL"
date:   2016-08-07 10:00:00
categories: jgroups unicast postgresql jdbc ping cluster
tags: regular
---

If you are trying to get your cluster to work over unicast, if you are using PostgreSQL as database and if you are trying to figure it out the right configurations to use, look no more, you arrived to the right place!

As you should know, JGroups offers you several options for cluster members discovery, some good examples are TCP_Ping, S3_Ping, File_Ping and JDBC_Ping. Not going to deep on why choosing one option over the other, one thing you should keep in mind is the dynamic aspect of this process. Usually, you want to be able to add or remove cluster nodes dynamically without having to change any configurations on your system, and to achieve that, you can use any of the last three options (TCP_Ping is more static in the sense that you will need to specify the hosts of all your cluster members).

As [JDBC_Ping](http://www.jgroups.org/manual/html/protlist.html#d0e5196) is a good option to use for discovery and I recently needed to configure it with PostgreSQL DB, and also didn't find anything on the web about the required configuration with the specifics for this database engine, I thought it could be useful to leave here the end result of it.

What you will need to do is to add this JDBC_Ping configuration section to your JGroups XML configuration file:


    <JDBC_PING  connection_url="jdbc:postgresql://<DB_SERVER_IP>:5432/<DB_NAME>" 
        connection_username="<DB_USER>"
        connection_password="<DB_PASSWORD>"
        connection_driver="org.postgresql.Driver"
        initialize_sql="CREATE TABLE IF NOT EXISTS JGROUPSPING (
                       own_addr varchar(200) NOT NULL,
                       bind_addr varchar(200) NOT NULL,
                       created timestamp NOT NULL,
                       cluster_name varchar(200) NOT NULL,
                       ping_data BYTEA,
                       constraint PK_JGROUPSPING PRIMARY KEY (own_addr, cluster_name)
                       )"
       insert_single_sql="INSERT INTO JGROUPSPING (own_addr, bind_addr, created, cluster_name, ping_data) values (?,'${jgroups.tcp.address:127.0.0.1}',NOW(), ?, ?)"
       delete_single_sql="DELETE FROM JGROUPSPING WHERE own_addr=? AND cluster_name=?"
       select_all_pingdata_sql="SELECT ping_data FROM JGROUPSPING WHERE cluster_name=?" />


And you should be ready to go! you can find more about JDBC_Ping configuration [here](https://developer.jboss.org/wiki/JDBCPING?_sscc=t) (Example: how to use datasource instead of connection url).


