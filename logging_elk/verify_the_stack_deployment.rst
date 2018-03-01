..  _elk_verify_the_stack_deployment:

Verify the Elastic stack deployment
===================================

Wait about a minute for the Elastic Stack to be created.

1. Run the following **docker stack services** command on the swarm manager to display the stack services.

    ..  code-block:: bash

        docker stack services elk

    Example output:

    ..  code-block:: text

        ID                  NAME                  MODE                REPLICAS            IMAGE                                                          PORTS
        45w4jhc02cqg        elk_elastic-search    replicated          1/1                 docker.elastic.co/elasticsearch/elasticsearch-platinum:6.2.2   *:9200->9200/tcp
        hydi27jhka4o        elk_kibana            replicated          1/1                 docker.elastic.co/kibana/kibana:6.2.2                          *:5601->5601/tcp
        iqd4d355j2y9        elk_logstash          replicated          1/1                 docker.elastic.co/logstash/logstash:6.2.2                      *:5000->5000/tcp
        uwn3o7w63eb9        elk_elastic-search2   replicated          1/1                 docker.elastic.co/elasticsearch/elasticsearch-platinum:6.2.2

2. Run the following **docker service ps** command on the swarm manager to display where the services are running and their statuses.

    ..  code-block:: bash

        docker stack ps elk

    Example output:

    ..  code-block:: text

        ID                  NAME                    IMAGE                                                          NODE                DESIRED STATE       CURRENT STATE           ERROR               PORTS
        ye8ddkb8a959        elk_elastic-search.1    docker.elastic.co/elasticsearch/elasticsearch-platinum:6.2.2   manager             Running             Running 2 minutes ago
        3b2p998xhpi0        elk_kibana.1            docker.elastic.co/kibana/kibana:6.2.2                          worker2             Running             Running 2 minutes ago
        yliof9n1jlod        elk_logstash.1          docker.elastic.co/logstash/logstash:6.2.2                      manager             Running             Running 2 minutes ago
        zee3nry4injj        elk_elastic-search2.1   docker.elastic.co/elasticsearch/elasticsearch-platinum:6.2.2   worker2             Running             Running 2 minutes ago

3. Run the following **docker service logs** commands on the swarm manager to display the logs for the services and check them for errors.

    ..  code-block:: bash

        docker service logs elk_elastic-search

    ..  code-block:: bash

        docker service logs elk_ elk_logstash

    ..  code-block:: bash

        docker service logs elk_kibana

4. You can run the following **curl** command on any docker node in the swarm to verify that the Elasticsearch cluster is up and running. 

    You will be prompted for the Elastic password which was specified in the :ref:`docker-compose.yml<elk_docker_compose_yml>` file in the environment for the Elasticsearch service.

    ..  code-block:: bash

        curl -u elastic 'http://127.0.0.1:9200'

    ..  code-block:: text

        Enter host password for user 'elastic':
   
    Example output:       

    ..  code-block:: json

        {
            "name" : "Shd_IQn",
            "cluster_name" : "docker-cluster",
            "cluster_uuid" : "BBQsv2KnSeehMwXTMeH5Jw",
            "version" : {
                "number" : "6.2.2",
                "build_hash" : "10b1edd",
                "build_date" : "2018-02-16T19:01:30.685723Z",
                "build_snapshot" : false,
                "lucene_version" : "7.2.1",
                "minimum_wire_compatibility_version" : "5.6.0",
                "minimum_index_compatibility_version" : "5.0.0"
            },
            "tagline" : "You Know, for Search"
        }

5. You can run the following **curl** command on any docker node in the swarm to check the status and health of the Elasticsearch cluster.

    You will be prompted for the Elastic password which was specified in the :ref:`docker-compose.yml<elk_docker_compose_yml>` file in the environment for the Elasticsearch service.

    .. code-block:: bash

        curl -s -u elastic 'http://127.0.0.1:9200/_cluster/health' | jq

    Example output:

    ..  code-block:: json
        :emphasize-lines: 3,16    

        {
            "cluster_name": "docker-cluster",
            "status": "green",
            "timed_out": false,
            "number_of_nodes": 2,
            "number_of_data_nodes": 2,
            "active_primary_shards": 4,
            "active_shards": 8,
            "relocating_shards": 0,
            "initializing_shards": 0,
            "unassigned_shards": 0,
            "delayed_unassigned_shards": 0,
            "number_of_pending_tasks": 0,
            "number_of_in_flight_fetch": 0,
            "task_max_waiting_in_queue_millis": 0,
            "active_shards_percent_as_number": 100
        }
     
    The **status** should be **green** and **active_shards_percent_as number** should be **100**.     

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
