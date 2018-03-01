..  _elk_enable_bootstrap_mem_lock:

..  raw:: latex

    \newpage

Enable bootstrap.mem_lock
=========================

Disabling swapping by enabling **bootstrap.mem_lock** needs to be configured in :ref:`Elasticsearch<elk_enable_bootstrap_mem_lock_elastic>` and :ref:`Docker<elk_enable_bootstrap_mem_lock_docker>`.

..  _elk_enable_bootstrap_mem_lock_elastic:

Elasticsearch
-------------

Disabling swapping in Elasticsearch is done by specifying the configuration parameter
**bootstrap.memory_lock=true** to Elasticsearch. This configuration parameter can be specified as an
environment parameter on the Elasticsearch services in the :ref:`docker-compose.yml<elk_docker_compose_yml>` file which will be used
to deploy the Elastic stack.

There is a cluster of 2 Elasticsearch services defined in the :ref:`docker-compose.yml<elk_docker_compose_yml>` file where the following is configured.

    ..  note:: The sample :ref:`docker-compose.yml<elk_docker_compose_yml>` file has this already configured.

    ..  code-block:: yaml
        :emphasize-lines: 10    
  
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

    ..  code-block:: yaml
        :emphasize-lines: 8    
  
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

That will allow each Elasticsearch service to lock its entire address space into `RAM <https://en.wikipedia.org/wiki/Random-access_memory>`_.

..  _elk_enable_bootstrap_mem_lock_docker:


Docker
------

Elasticsearch will require a special operating system permission to lock its entire address space into `RAM <https://en.wikipedia.org/wiki/Random-access_memory>`_.
The Elasticsearch process is running as a docker container and so it inherits from the docker daemon. 
It is therefore necessary to grant this permission to the docker daemon. 
Out of the box after installation the docker daemon does not have this permission. 
If you attempt to start the Elasticsearch service and it fails, and you see this error message: '**memory
locking requested for elasticsearch process but memory is not locked**', you will need to grant
the docker daemon permission so Elasticsearch can lock its address space into `RAM <https://en.wikipedia.org/wiki/Random-access_memory>`_. 

To grant the docker daemon this permission requires a configuration setting and a restart of the docker daemon.
Issue the following command from a linux command prompt with root authority to check if the docker
daemon has the necessary permission:

    ..  code-block:: bash

        grep locked /proc/$(ps --no-headers -o pid -C dockerd | tr -d ' ')/limits

If the response returned does not match this below, it is necessary to perform the configuration change:

    ..  code-block:: text

        Max locked memory unlimited unlimited bytes

To perform the configuration change issue the following command from a linux command prompt with root authority:

    ..  code-block:: bash

        echo -e "[Service]\nLimitMEMLOCK=infinity" | SYSTEMD_EDITOR=tee systemctl edit docker.service

The response should be:

    ..  code-block:: text

        [Service]
        LimitMEMLOCK=infinity

Then issue the following command from a linux command prompt with root authority to enable the setting and restart the docker daemon.

    ..  code-block:: bash

        systemctl daemon-reload
        systemctl restart docker

Issue the following commands from a linux command prompt with root authority to check if the docker daemon now has the necessary permission:

    ..  code-block:: bash

        grep locked /proc/$(ps --no-headers -o pid -C dockerd | tr -d ' ')/limits

The response should now look like this:

    ..  code-block:: text

        Max locked memory unlimited unlimited bytes

You will need to perform this configuration check and setup on all docker nodes where you will be deploying the Elasticsearch service on.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
    