..  _splunk_overview:

Solution Brief Overview
=======================

`Splunk <https://www.splunk.com/>`_ is a software platform to gather, store, search, analyze and visualize the machine-generated
data gathered from the websites, applications, databases, sensors, devices etc. which make up your IT
infrastructure and business.

Splunk allows you to collect your data in real time from multiple remote systems, analyze and correlate
it, and quickly search and display it. The data can be in any format - log files, text files - csv, json, etc.

With Splunk you can:

* Analyze the performance of your systems and applications
* Troubleshoot performance problems and failures
* Verify security compliance
* Detect security threats and breaches
* Monitor business metrics
* Create dashboards to visualize the data analysis
* Generate alerts
* Store and retrieve the data for later use

Splunk Architecture
-------------------

Splunk consists of the following 3 main components:

1. `Forwarder <http://docs.splunk.com/Documentation/Splunk/7.0.2/Forwarding/Typesofforwarders>`_ - collects the logs from remote machines and forwards the data to indexers

    * Universal Forwarder - performs minimal processing and forwards the raw data
    * Heavy Forwarder - performs parsing and indexing at the source and forwards the processed data

2. `Indexer <http://docs.splunk.com/Splexicon:Indexer>`_ - parses and indexes the log data, and stores it for analysis and searching
3. `Search Head <https://docs.splunk.com/Splexicon:Searchhead>`_ - graphical user interface for searching and displaying the log data

Optional components:

* `Monitoring Console <https://docs.splunk.com/Documentation/Splunk/7.0.2/DMC/DMCoverview>`_ - lets you view detailed topology and performance information about your Splunk Enterprise deployment.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1