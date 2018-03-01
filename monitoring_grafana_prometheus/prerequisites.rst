..  _grafana_prometheus_monitoring_prerequisites:

Prerequisites
=============

Build a custom Nginx docker image
---------------------------------

The Prometheus service does not include built-in authentication or any other general purpose security mechanism, so the Prometheus metrics endpoint is wide open. 

In this solution brief a Nginx service will be deployed to one node in the swarm to be used as a reverse proxy with `basic authentication <https://en.wikipedia.org/wiki/Basic_access_authentication>`_ to secure Prometheus.

You will need to build a custom Nginx docker image to use in this deployment.

Bring up a Linux command prompt with root authority and run the following steps/commands

1. Launch an Nginx docker container as a daemon in the background from the Docker Official `Nginx <https://hub.docker.com/_/nginx/>`_ docker image.
     
    ..  code-block:: bash

        docker container run -d --name nginx nginx:latest

2. Get a command prompt inside the **nginx** container.

    ..  code-block:: bash

        docker container exec -it nginx bash

3. Install the **htpasswd** command inside the running **nginx** container.

    ..  code-block:: bash

        apt-get update -qq;apt-get install apache2-utils -y

4. Change into the **/etc/nginx** directory.

    ..  code-block:: bash

        cd /etc/nginx

5. Create a user named **prometheus** to secure Prometheus using the **htpasswd** command.

    You will be prompted for the new password. Remember the password as you will need it later when configuring the :ref:`Prometheus data source<grafana_prometheus_monitoring_define_prometheus_as_data_source>` from the Grafana web interface.

    ..  code-block:: bash

        htpasswd -c .htpasswd prometheus

    ..  code-block:: text

        New password:
        Re-type new password:

    ..  code-block:: text

        Adding password for user prometheus

6. Secure the **.htpasswd** file by changing the permissions to 644.

    ..  code-block:: bash

        chmod 644 .htpasswd

7. Exit out of the Nginx container.

    ..  code-block:: bash

        exit

8. Stop the Nginx container.

    ..  code-block:: bash

        docker container stop nginx

9. Now make a new docker image from the Nginx container. From the Linux command prompt run the following command:

    ..  code-block:: bash

        docker container commit nginx monitoring_nginx:latest

10. You need to tag and push that image up to your private Docker registry.

    In in this Solution Brief I'm pushing the custom Nginx docker image to Docker Hub in my Docker Hub account ``gforghetti``.

    .. code-block:: bash

        docker image tag monitoring_nginx:latest gforghetti/monitoring_nginx:latest
        docker image push gforghetti/monitoring_nginx:latest

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
    
