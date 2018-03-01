..  _grafana_prometheus_monitoring_volume_usage:

Volume usage
============

1. The Grafana service stores it's persistent data (sqlite3 database containing dashboards and users) on 1 volume.

    * **/var/lib/grafana**

2. The Prometheus service stores it's persistent data (metrics) on 1 volume.

    * **/prometheus**

3. The cAdvisor Service uses the following volumes (read only) so it can scrape system metrics, issue docker commands (top, stats, event, inspect) and access docker container information and logs in order to do the monitoring.

    * **/**
    * **/var/run**
    * **/sys**
    * **/var/lib/docker/**

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
    
   