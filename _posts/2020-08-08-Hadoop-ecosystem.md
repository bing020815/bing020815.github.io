---
layout: post
title: "Database Management: Hadoop Ecosystem"
date: 2020-08-08
theme: minimal
mathjax: true
categories: Database
---

<div id='top'>
  <p align="center"><img src="{{site.baseurl}}/assets/images/post/database/hadoop-ecosystem.png" title=""></p>
  <p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Hadoop Ecosystem</p>
</div>

## Hadoop 
When we talk about **big data**, we often think of Hadoop. Why? Hadoop is a system for <u>storing data</u>, <u>processing data</u> and <u>managing data</u>. It can ingest data from different platform or resources. In the big data world, sometimes, the traditional DBMSs could not meet their reporting requirements. Companies may require to shorten the time to process a significant amount of data. Increasing more storage or computer power could be another benefit using Hadoop. 

Hadoop consists of three basic parts:
* **HDFS**: storing data
* **YARN**: managing data
* **MapReduce**: processing data

Hadoop implements cluster management in the system. It stores data and process data in clusters. Each cluster contains a master node and worker nodes. The master node runs the Apache Yarn as **Resource Manager**. The worker node runs Apache Yarn as **Node Manager** to getting the information of CPU, memory, disk and network usage to the **Resource Manager**. The **Resource Manager** decides where to direct the new tasks based on the current workloads reported from **Node Manager** with the Scheduler and ApplicationsManager.

<p align="center"><img src="{{site.baseurl}}/assets/images/post/database/cluster.png" title=""></p>

Hadoop Data are:
* Time-variant: reflect that point in time
* Non-volatile: not updated
* Subject-oriented: stored by topic

The example of hadoop data are web logs, sales transactions, event records, sensor data...etc

<br>

### The Hadoop Philosophy

* Capture the data “as are” and store them.
* Do not transform before you store them.
* Store all the data, as you don’t know what you’ll need.
* Transform them when you query them.

This is the anti-pattern of relational modeling!

<br>

### How Does Hadoop Differ From Relational?

  <div id="relation_vs_hadoop">
  <style>
  table {border: none; width: 100%; table-layout: fixed ;}
  </style>
  <table cellspacing="0" cellpadding="0">
  <thead>
  <tr>
  <th align="center">Relational</th>
  <th align="center">Hadoop</th>
  </tr>
  </thead>

  <tbody> <tr>
  <td>
  	<ul style="list-style: none">
  		<li>1. Schema on write; need a table</li>
  		<li>2. Fast reads</li>
  		<li>3. Highly structured data</li>
  		<li>4. Declarative data processing(SQL)</li>
  		<li>5. Good for ACID transactions, business data</li>
  	</ul>
  </td>
  <td>
  	<ul style="list-style: none">
  		<li>1. Schema on read; schema applied when data are read</li>
  		<li>2. Fast writes</li>
  		<li>3. Loosely structured data; write the data “as they are” to HDFS</li>
  		<li>4. Declarative and procedural data processing</li>
  		<li>5. Good for logs, data streams, unstructured data discovery</li>
  	</ul>
  </td>
  </tr>  </tbody>   
  </table>
  </div>

<strong>Note: ACID (Atomicity, Consistency, Isolation, Durability)</strong>

<br>

### MapReduce
MapReduce is a processing technique and a program model for distributed computing based on java. Map takes a set of data and converts it into another set of data, where individual elements are broken down into tuples (key/value pairs).
* **Map**: apply a transformation to a data set
* **Shuffle**: transfer output from Mapper to Reducer nodes
* **Reduce**: aggregate items into a single result
* **Combine**: output of Reducer nodes into single output

<p align="center"><img src="{{site.baseurl}}/assets/images/post/database/mapreduce.png" title="" style="width: 60%"></p>
<p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">MapReduce process</p>

<br>

### HDFS
The Hadoop Distributed File System (HDFS) is a distributed file system designed to run on commodity hardware. It is highly fault-tolerant and is designed to be deployed on low-cost hardware. HDFS provides high throughput access to application data and is suitable for applications that have large data sets. 

HDFS is reponsible for: 
* Distributed data storage paradigm
* A single file is divided into blocks
* Blocks are spread across nodes
* Blocks are written multiple times for redundancy

<p align="center"><img src="{{site.baseurl}}/assets/images/post/database/abc.png" title=""></p>
<p align="center"><img src="{{site.baseurl}}/assets/images/post/database/HDFS.png" title="" ></p>

<br>

## Hadoop Ecosystem in Action

<p align="center"><img src="{{site.baseurl}}/assets/images/post/database/ecosystem.png" title="" style="width: 90%"></p>
<p align="center" style="font-size: 0.8em; color: grey; font-style: italic;">Hadoop Ecosystem in Action</p>

<br>

## Options for Data Ingestion

<p align="center"><img src="{{site.baseurl}}/assets/images/post/database/data_ingestion.png" title="" style="width: 75%"></p>

<p align="center"><a href="#top">Top</a></p>
