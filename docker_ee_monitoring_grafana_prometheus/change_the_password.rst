..  _grafana_prometheus_monitoring_change_the_password:

..  raw:: latex

    \newpage

Change the Grafana password
============================

The Grafana password is hardcoded in the :ref:`docker-compose.yml<grafana_prometheus_monitoring_docker_compose_yml>` file. Change the password to a more secure value.

    **Grafana** service

    .. code-block:: yaml
        :emphasize-lines: 11

        monitoring_grafana:
            image: grafana/grafana:latest
            hostname: monitoring_grafana
            networks:
                - monitoring-frontend
                - monitoring-backend  
            ports:
                - "3000:3000"      
            environment:
                - GF_SECURITY_ADMIN_USER=admin
                - GF_SECURITY_ADMIN_PASSWORD=Passw0rd#
            volumes:
                - grafana-data:/var/lib/grafana
            depends_on:
                - monitoring_prometheus  

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
    