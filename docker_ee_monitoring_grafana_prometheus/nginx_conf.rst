..  _grafana_prometheus_monitoring_nginx_conf:

..  raw:: latex

    \newpage

Download the nginx.conf file
============================

This is a sample **nginx.conf** configuration file which configures Nginx as a reverse proxy with `basic authentication <https://en.wikipedia.org/wiki/Basic_access_authentication>`_.
It must exist in the same directory as the :ref:`docker-compose.yml<grafana_prometheus_monitoring_docker_compose_yml>` file. 

Click :download:`here <samples/nginx.conf>` to download the sample **nginx.conf** file.

..  literalinclude:: samples/nginx.conf
    :language: text   

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
       