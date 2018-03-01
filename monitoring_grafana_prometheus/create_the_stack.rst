..  _grafana_prometheus_monitoring_create_the_stack:

..  raw:: latex

    \newpage

Create the Grafana/Prometheus stack
===================================

Run the following **docker stack deploy** command on the swarm manager to create the Grafana/Prometheus stack:

    ..  code-block:: bash

        docker stack deploy -c docker-compose.yml prometheus

Example output:

    .. code-block:: text

        Creating network prometheus_monitoring-backend
        Creating service prometheus_monitoring_grafana
        Creating service prometheus_monitoring_prometheus
        Creating service prometheus_monitoring_node_exporter
        Creating service prometheus_monitoring_cadvisor
        Creating service prometheus_monitoring_nginx
   
..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
       