..  _grafana_prometheus_monitoring_change_nginx_docker_image:

..  raw:: latex

    \newpage

Change the Nginx docker image
==============================

Modify the :ref:`docker-compose.yml<grafana_prometheus_monitoring_docker_compose_yml>` file and replace the **monitoring_nginx** service docker image
with the custom :ref:`Nginx<grafana_prometheus_monitoring_prerequisites>` docker image you built previously.

    **Nginx** service

    .. code-block:: yaml
        :emphasize-lines: 2

        monitoring_nginx:
          image: gforghetti/monitoring_nginx:latest

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
    