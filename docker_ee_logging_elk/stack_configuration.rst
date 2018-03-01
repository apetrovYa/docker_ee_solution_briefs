..  _elk_logging_stack_configuration:

Elastic Stack Configuration
===========================

This solution brief will deploy an Elastic stack consisting of the following docker services.

* A cluster of two Elasticsearch services will be deployed in the swarm.
* A single Logstash service will be deployed in the swarm and configured to collect logs from docker containers running with the `Docker Syslog logging driver <https://docs.docker.com/config/containers/logging/syslog/>`_ and send the logs to the Elasticsearch cluster.
* A single Kibana service will be deployed in the swarm and configured to visualize the logs stored in Elasticsearch.

The docker images for all services are provided by `Elastic <https://www.docker.elastic.co/>`_.

An example will be shown on how to use the `Docker Syslog logging driver <https://docs.docker.com/config/containers/logging/syslog/>`_ to capture the logs from Docker containers and send them to the Elastic stack.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
