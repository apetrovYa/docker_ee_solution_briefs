..  _elk_change_the_password:

..  raw:: latex

    \newpage

Change the Elasticsearch password
=================================

The Elasticsearch password is hardcoded in the :ref:`docker-compose.yml<elk_docker_compose_yml>` file in 3 places. Change the password to a more secure value, make sure all 3 match.

    **Elastic** service

    ..  code-block:: yaml
        :emphasize-lines: 3

        elastic-search:
          environment:
            - ELASTIC_PASSWORD=Passw0rd#

    **Logstash** service

    ..  code-block:: yaml
        :emphasize-lines: 4

        logstash:
          environment:  
            - 'xpack.monitoring.elasticsearch.username=elastic'
            - 'xpack.monitoring.elasticsearch.password=Passw0rd#'          

    **Kibana** service

    ..  code-block:: yaml
        :emphasize-lines: 6

        kibana:
          environment:  
            - SERVER_NAME=kibana
            - ELASTICSEARCH_URL=http://elastic-search:9200
            - ELASTICSEARCH_USERNAME=elastic
            - ELASTICSEARCH_PASSWORD=Passw0rd#    

There is also an Elasticsearch password hardcoded in the :ref:`logstash.conf<elk_logstash_conf>` file for Elasticsearch. Make sure it matches the Elasticsearch service **elastic-search** password value.  

    **logstash.conf**

    ..  literalinclude:: samples/logstash.conf
        :language: text  
        :emphasize-lines: 13                         

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
     