..  _grafana_prometheus_monitoring_overview:

Solution Brief Overview
=======================

Prometheus
----------

..  _prometheus_overview:

`Prometheus <https://prometheus.io/>`_ is an open source monitoring system which stores all its data in a time series database and
offers a multi-dimensional data-model and a powerful query language.

Prometheus's main features are:

* A multi-dimensional data model with time series data identified by metric name and key/value pairs
* A flexible query language to leverage this dimensionality
* No reliance on distributed storage; single server nodes are autonomous
* Time series collection happens via a pull model over HTTP
* Pushing time series is supported via an intermediary gateway
* Targets are discovered via service discovery or static configuration
* Multiple modes of graphing and dashboarding support

The Prometheus ecosystem consists of multiple components, many of which are optional:

* The main Prometheus server which scrapes and stores time series data
* client libraries for instrumenting application code
* A push gateway for supporting short-lived jobs
* Special-purpose exporters for services like HAProxy, StatsD, Graphite, etc.
* An alertmanager to handle alerts
* Various support tools

Prometheus scrapes metrics from instrumented jobs, either directly or via an intermediary push
gateway for short-lived jobs. It stores all scraped samples locally and runs rules over this data to either
aggregate and record new time series from existing data or generate alerts. Grafana or other API
consumers can be used to visualize the collected data.

..  _grafana_overview:

Grafana
-------

`Grafana <https://grafana.com/>`_ is an open source metric analytics and visualization suite. It is most commonly used for
visualizing time series data for infrastructure and application analytics.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
    