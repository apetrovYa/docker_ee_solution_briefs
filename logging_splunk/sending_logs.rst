..  _splunk_sending_logs:

Send Docker container logs to the Splunk Stack
==============================================

To test the Splunk **HTTP Event Collector** you can run the following **docker container run** command to start an Apache HTTP Web Server container with the `Splunk Docker Logging Driver <https://docs.docker.com/config/containers/logging/splunk/>`_. 
Substitute ``splunk-http-event-collector-token`` with the previously created **HTTP Event Collector** token. Substitute ``docker-node-name`` with the hostname of the docker node where the Splunk Enterprise server service is running.

    .. code-block:: bash
        :emphasize-lines: 7,10  

        docker container run \
        -d --rm --name apache \
        --network splunk_splunk-backend \
        --hostname apache-server \
        -p 80:80 \
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
  