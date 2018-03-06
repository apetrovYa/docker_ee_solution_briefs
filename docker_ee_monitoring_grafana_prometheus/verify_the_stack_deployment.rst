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
        hie1o6s89mk7        prometheus_monitoring_cadvisor        global              4/4                 google/cadvisor:latest               *:8080->8080/tcp
        mwd068x8winp        prometheus_monitoring_nginx           replicated          1/1                 gforghetti/monitoring_nginx:latest   *:19090->19090/tcp
        q4el1tam91gz        prometheus_monitoring_prometheus      replicated          1/1                 prom/prometheus:latest
        scov4jrjdfu2        prometheus_monitoring_node_exporter   global              4/4                 prom/node-exporter:latest            *:9100->9100/tcp
        vmmhcn2uelz5        prometheus_monitoring_grafana         replicated          1/1                 grafana/grafana:latest               *:3000->3000/tcp

2. Run the following **docker service ps** command on the swarm manager to display where the services are running and their statuses.

    ..  code-block:: bash

        docker stack ps prometheus

    Example output:

    ..  code-block:: text

        ID                  NAME                                                            IMAGE                                NODE                DESIRED STATE       CURRENT STATE           ERROR               PORTS
        b4l9tz80wh2c        prometheus_monitoring_cadvisor.pkydswz5708zvth3ok1migziq        google/cadvisor:latest               worker1             Running             Running 1 minutes ago
        phjhu4fc8fen        prometheus_monitoring_cadvisor.rdb0f9hgsi7533puaoi1mapln        google/cadvisor:latest               manager             Running             Running 1 minutes ago
        t5xm7m30kumk        prometheus_monitoring_cadvisor.6dbmhj26ydctir5se6no0zewe        google/cadvisor:latest               worker3.acme.com    Running             Running 1 minutes ago
        movwpnotn9fe        prometheus_monitoring_cadvisor.34usz92cx71n6nj2ahum95ojr        google/cadvisor:latest               worker2.acme.com    Running             Running 1 minutes ago
        q51uyr1rqoqk        prometheus_monitoring_node_exporter.6dbmhj26ydctir5se6no0zewe   prom/node-exporter:latest            worker3.acme.com    Running             Running 1 minutes ago
        oh6en98g60aj        prometheus_monitoring_node_exporter.34usz92cx71n6nj2ahum95ojr   prom/node-exporter:latest            worker2.acme.com    Running             Running 1 minutes ago
        uf990f56n7is        prometheus_monitoring_node_exporter.pkydswz5708zvth3ok1migziq   prom/node-exporter:latest            worker1             Running             Running 1 minutes ago
        0id5i3v0xj70        prometheus_monitoring_node_exporter.rdb0f9hgsi7533puaoi1mapln   prom/node-exporter:latest            manager             Running             Running 1 minutes ago
        sixswn6paq8n        prometheus_monitoring_prometheus.1                              prom/prometheus:latest               worker2.acme.com    Running             Running 1 minutes ago
        r7lp2av2hg5h        prometheus_monitoring_grafana.1                                 grafana/grafana:latest               worker3.acme.com    Running             Running 1 minutes ago
        72hdx9tcdlgz        prometheus_monitoring_nginx.1                                   gforghetti/monitoring_nginx:latest   manager             Running             Running 1 minutes ago

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
    