..  _elk_increase_file_descriptors:

..  raw:: latex

    \newpage

Increase file descriptors
=========================

In a production environment it is important to ensure that increased `ulimits <https://kerneltalks.com/linux/ulimit-value-need-know/>`_ for **nofile** (number of open files) are available for
the Elasticsearch services. This can be configured by setting the **nofile** configuration parameter on the
Elasticsearch services in the :ref:`docker-compose.yml<elk_docker_compose_yml>` file used to bring up the Elastic stack. 

There is a cluster of 2 Elasticsearch services defined in the :ref:`docker-compose.yml<elk_docker_compose_yml>` file where the following is configured:

    ..  note:: The sample :ref:`docker-compose.yml<elk_docker_compose_yml>` file has this already configured.

    ..  code-block:: yaml
        :emphasize-lines: 13,18-20

        elastic-search:
          image: docker.elastic.co/elasticsearch/elasticsearch-platinum:6.2.2
          hostname: elastic-search
          volumes:
            - elasticdata1:/usr/share/elasticsearch/data
          ports:
            - 9200:9200
          environment:
            - cluster.name=docker-cluster
            - bootstrap.memory_lock=true
            - "ES_JAVA_OPTS=-Xms1024m -Xmx1024m"
            - ELASTIC_PASSWORD=Passw0rd#
          ulimits:
            nproc: 65535
            memlock:
              soft: -1
              hard: -1 
            nofile: 
              soft: 65536
              hard: 65536

    ..  code-block:: yaml
        :emphasize-lines: 11,16-18

        elastic-search2:
          image: docker.elastic.co/elasticsearch/elasticsearch-platinum:6.2.2
          hostname: elastic-search2
          volumes:
            - elasticdata2:/usr/share/elasticsearch/data
          environment:
            - cluster.name=docker-cluster
            - bootstrap.memory_lock=true
            - "ES_JAVA_OPTS=-Xms1024m -Xmx1024m"
            - "discovery.zen.ping.unicast.hosts=elastic-search"
          ulimits:
            nproc: 65535
            memlock:
              soft: -1
              hard: -1 
            nofile: 
              soft: 65536
              hard: 65536

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
    
   