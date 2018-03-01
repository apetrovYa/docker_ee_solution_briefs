..  _splunk_logging_stack_configuration:

Splunk Stack Configuration
==========================
 
This solution brief will deploy a Splunk stack consisting of the following docker services.

* A `Splunk Enterprise server <http://docs.splunk.com/Documentation/Splunk/7.0.2/Deploy/Distributedoverview>`_ service will be deployed on the swarm manager node which will contain an `indexer <http://docs.splunk.com/Splexicon:Indexer>`_ and `search head <http://docs.splunk.com/Splexicon:Searchhead>`_.
* A `Splunk Universal Forwarder <http://docs.splunk.com/Documentation/Forwarder/7.0.2/Forwarder/Abouttheuniversalforwarder>`_ service will be run on each swarm worker node.

An example will be shown on how to use the `Splunk Docker Logging Driver <https://docs.docker.com/config/containers/logging/splunk/>`_ to capture the logs from
Docker containers and send them to the Splunk stack.

The docker images for all of the services are provided by `Splunk <https://www.splunk.com/en_us/products/splunk-enterprise.html>`_.

..  note:: The Splunk docker images on Docker Store are old and are not being updated regularly by
    Splunk. Therefore, the Splunk Docker Hub docker images are being used in this Solution Brief.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
    