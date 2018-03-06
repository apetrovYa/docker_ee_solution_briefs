..  _splunk_sending_logs:

Send Docker container logs to the Splunk Stack
==============================================

To send docker container logs to the Splunk **HTTP Event Collector** you can run the following **docker service create** command on the swarm manager to start an Apache HTTP Web Server service with the `Splunk Docker Logging Driver <https://docs.docker.com/config/containers/logging/splunk/>`_. 
Substitute ``splunk-http-event-collector-token`` with the previously created **HTTP Event Collector** token. Substitute ``docker-node-name`` with the hostname of any docker node in the swarm.

    .. code-block:: bash
        :emphasize-lines: 8,11  

        docker service create --detach \
        --name apache \
        --network splunk_splunk-backend
        --hostname apache.acme.com  \
        --publish 80:80 \
        --replicas 1 \
        --log-driver=splunk \
        --log-opt splunk-token=splunk-http-event-collector-token \
        --log-opt tag="{{.Name}}/{{.FullID}}" \
        --log-opt splunk-insecureskipverify=true \
        --log-opt splunk-url="https://docker-node-name:8088" \
        httpd

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
  