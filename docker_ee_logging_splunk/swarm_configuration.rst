..  _splunk_swarm_configuration:

Docker EE Swarm Configuration
=============================

A Splunk stack will be deployed to the following 3 node Docker Swarm.

* A `Splunk Enterprise server <http://docs.splunk.com/Documentation/Splunk/7.0.2/Deploy/Distributedoverview>`_ service will be deployed on the swarm manager node which will contain an `indexer <http://docs.splunk.com/Splexicon:Indexer>`_ and `search head <http://docs.splunk.com/Splexicon:Searchhead>`_.
* A `Splunk Universal Forwarder <http://docs.splunk.com/Documentation/Forwarder/7.0.2/Forwarder/Abouttheuniversalforwarder>`_ service will be run on each swarm worker node.


..  image:: images/docker_swarm_configuration.png

The services must be separated and run on different Docker nodes.

* Placement constraints will be used in the :ref:`docker-compose.yml<splunk_docker_compose_yml>` file to ensure that the Splunk Enterprise Server service runs on the swarm manager node.

    * constraints: [node.role==manager]

* Placement constraints and global services will be used in the :ref:`docker-compose.yml<splunk_docker_compose_yml>` file to ensure that one Splunk Forwarder service runs on all worker nodes.

    * constraints: [node.role==worker]
    * mode:global

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
