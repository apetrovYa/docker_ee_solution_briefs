..  _grafana_prometheus_monitoring_verify_the_stack_deployment:

Verify the Grafana/Prometheus stack deployment
==============================================

Wait about a minute for the Grafana/Prometheus Stack to be created.

1. Run the following **docker stack services** command on the swarm manager to display the stack services.

    ..  code-block:: bash

        docker stack services prometheus

    Example output:

    ..  code-block:: text

        ID                  NAME                                  MODE                REPLICAS            IMAGE                                PORTS
        8lkr1k10n3k1        prometheus_monitoring_prometheus      replicated          1/1                 prom/prometheus:latest
        f0w2opzilook        prometheus_monitoring_grafana         replicated          1/1                 grafana/grafana:latest               *:3000->3000/tcp
        nljzxf3lyk4p        prometheus_monitoring_cadvisor        global              3/3                 google/cadvisor:latest               *:8080->8080/tcp
        nn9ed9ns63cg        prometheus_monitoring_nginx           replicated          1/1                 gforghetti/monitoring_nginx:latest   *:19090->19090/tcp
        rcd4pspbo2x1        prometheus_monitoring_node_exporter   global              3/3                 prom/node-exporter:latest            *:9100->9100/tcp

2. Run the following **docker service ps** command on the swarm manager to display where the services are running and their statuses.

    ..  code-block:: bash

        docker stack ps prometheus

    Example output:

    ..  code-block:: text

        ID                  NAME                                                            IMAGE                                NODE                DESIRED STATE       CURRENT STATE                ERROR               PORTS
        p6x5viady3wb        prometheus_monitoring_node_exporter.borj0fhi37ecii1q7jub6sv8o   prom/node-exporter:latest            worker2             Running             Running 58 seconds ago
        douj51t6ahik        prometheus_monitoring_node_exporter.u4p80of52ks9m547vzsprfmwp   prom/node-exporter:latest            worker1             Running             Running about a minute ago
        qbk26pmngqbb        prometheus_monitoring_node_exporter.vuphc2eu6jtf0lway74owo2q8   prom/node-exporter:latest            manager             Running             Running 54 seconds ago
        x2x1crewimef        prometheus_monitoring_cadvisor.borj0fhi37ecii1q7jub6sv8o        google/cadvisor:latest               worker2             Running             Running about a minute ago
        qu1izkl7ntpc        prometheus_monitoring_cadvisor.u4p80of52ks9m547vzsprfmwp        google/cadvisor:latest               worker1             Running             Running about a minute ago
        jb8s5qt3n4qm        prometheus_monitoring_cadvisor.vuphc2eu6jtf0lway74owo2q8        google/cadvisor:latest               manager             Running             Running 58 seconds ago
        hdl7blhjdasq        prometheus_monitoring_prometheus.1                              prom/prometheus:latest               manager             Running             Running 55 seconds ago
        j5ebf76vb95n        prometheus_monitoring_grafana.1                                 grafana/grafana:latest               worker2             Running             Running 50 seconds ago
        kycr2i28cr2t        prometheus_monitoring_nginx.1                                   gforghetti/monitoring_nginx:latest   manager             Running             Running 52 seconds ago

3. Run the following **docker service logs** commands on the swarm manager to display the logs for the services and check them for errors.

    ..  code-block:: bash

        docker service logs prometheus_monitoring_nginx

    ..  code-block:: bash

        docker service logs prometheus_monitoring_prometheus

    ..  code-block:: bash

        docker service logs prometheus_monitoring_grafana

    ..  code-block:: bash

        docker service logs prometheus_monitoring_cadvisor

    ..  code-block:: bash

        docker service logs prometheus_monitoring_node_exporter

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
    