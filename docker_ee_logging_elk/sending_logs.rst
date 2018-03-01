..  _elk_sending_logs:

Send Docker container logs to the Elastic Stack
===============================================
You can use the `Docker Syslog logging driver <https://docs.docker.com/config/containers/logging/syslog/>`_ to capture the logs of running docker containers and send them to the Logstash service running in the Elastic stack.

You can configure the Docker daemon with the default logging driver to be used for all docker containers and you can also configure the logging driver for a specific container. 
For more details refer to `Configure logging drivers <https://docs.docker.com/config/containers/logging/configure/>`_.

Syslog logging driver
---------------------

Here is an example of running a Docker container in the Docker Swarm where the Elastic stack is
running to use the `Docker Syslog logging driver <https://docs.docker.com/config/containers/logging/syslog/>`_. 
This docker container is running the Apache HTTP Server. 
Run the command below to send Apache HTTP Server logs to the Elastic stack.

    ..  code-block:: bash

        docker container run -d --name apache --log-driver=syslog --log-opt syslog-address=tcp://:5000 httpd:latest

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  