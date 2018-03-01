..  _elk_overview:

Solution Brief Overview
=======================

Elasticsearch
-------------

..  _elasticsearch_overview:

`Elasticsearch <https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html>`_ is an open-source, broadly-distributable, readily-scalable, enterprise-grade search engine
which can be used to search all kinds of documents. It provides scalable search, has near real-time
search, and supports multitenancy. Elasticsearch will be used to store the logs that are collected by Logstash.

..  _logstash_overview:

Logstash
--------

`Logstash <https://www.elastic.co/guide/en/logstash/current/introduction.html>`_ is a light-weight, open-source, server-side data processing pipeline that allows you to collect
data from a wide variety of sources, transform it on the fly, and send it to your desired destination.
Logstash will be configured to collect logs and send them to Elasticsearch.

..  _kibana_overiew:

Kibana
------

`Kibana <https://www.elastic.co/guide/en/kibana/current/introduction.html>`_ is an open-source data visualization and exploration tool used for log and time series analytics,
and application monitoring. Kibana will be configured and used to search and view the logs that Logstash 
has indexed and stored in Elasticsearch.

..  _xpack_overiew:

X-Pack
------

`X-Pack <https://www.elastic.co/guide/en/x-pack/current/xpack-introduction.html>`_ is an Elastic stack extension that bundles security, alerting, monitoring, reporting, and graph
capabilities into one easy-to-install package. The Elastic docker images used in this Solution Brief (Elasticsearch, Logstash and
Kibana) come with X-Pack pre-installed.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
    