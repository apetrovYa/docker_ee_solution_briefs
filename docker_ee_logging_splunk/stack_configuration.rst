..  _splunk_logging_stack_configuration:

Splunk Stack Configuration
==========================
 
This solution brief will deploy a Splunk stack in the docker swarm consisting of the following docker services which all must be run on separate nodes.

    * A single `Splunk Enterprise server <http://docs.splunk.com/Documentation/Splunk/7.0.2/Deploy/Distributedoverview>`_ service will be deployed on one node in the swarm which will contain an `indexer <http://docs.splunk.com/Splexicon:Indexer>`_ and `search head <http://docs.splunk.com/Splexicon:Searchhead>`_.
     
    * A `Splunk Universal Forwarder <http://docs.splunk.com/Documentation/Forwarder/7.0.2/Forwarder/Abouttheuniversalforwarder>`_ service will be deployed on each remaining node in the swarm.
        
    ..  note:: The Splunk Enterprise server and a Splunk Universal Forwarder server cannot run on the same node.

    ..  note:: Only one Splunk Universal Forwarder server can run on a node.

..  note:: The `Splunk <https://www.splunk.com/en_us/products/splunk-enterprise.html>`_ docker images on Docker Store are old and are not being updated regularly by
    Splunk. Therefore, the Splunk Docker Hub docker images are being used in this Solution Brief.

In order to ensure that the Splunk stack services run on separate nodes, placement constraints with labels will be used which requires labels to be added to the docker nodes in the swarm.

* Placement constraints with labels will be used in the :ref:`docker-compose.yml<splunk_download_docker_compose_yml>` file to ensure that the Splunk Enterprise Server service runs by itself on only one node in the swarm. 

    ..  code-block:: yaml
        :emphasize-lines: 7-11

        splunk-enterprise:
            image: splunk/splunk:7.0.0-monitor
            hostname: splunk-enterprise
            networks:
                - splunk-frontend  
                - splunk-backend  
            deploy:
                mode: replicated
                replicas: 1
                placement:
                    constraints: [node.labels.splunk-node-type==enterprise-server]      

* Placement constraints will labels and global services (``mode: global``) will be used in the :ref:`docker-compose.yml<splunk_download_docker_compose_yml>` file to ensure that one Splunk Forwarder service runs on all other nodes.

    ..  code-block:: yaml
        :emphasize-lines: 8-11

        splunk-forwarder:
            image: splunk/universalforwarder:7.0.0-monitor
            hostname: splunk-forwarder
            depends_on:
                - splunk-enterprise
            networks:
                - splunk-backend       
            deploy:
                mode: global
                placement:
                    constraints: [node.labels.splunk-node-type==forwarder-server]  

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
    