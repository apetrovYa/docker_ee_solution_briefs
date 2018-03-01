..  `grafana_prometheus_monitoring_stack_configuration:

Grafana/Prometheus Stack Configuration
======================================

This solution brief will deploy a Grafana/Prometheus stack to monitor all docker nodes and containers running in the swarm consisting of the following 5 services:

1. A **Nginx** server service will be deployed to one node in the swarm to be used as a reverse proxy with `basic authentication <https://en.wikipedia.org/wiki/Basic_access_authentication>`_ to secure Prometheus.
 
   | The Nginx server is a Docker Official Image maintained by the `Nginx Docker Maintainers <https://hub.docker.com/_/nginx/>`_.
   |

2. A **Grafana** server service will be deployed to one node in the swarm. 

   | The Grafana server is a Docker Hub docker image provided by `Grafana <https://hub.docker.com/r/grafana/grafana/>`_.
   |

3. A **Prometheus** server service will be deployed to one node in the swarm.

   | The Prometheus server is a Docker Hub docker image provided by `Prometheus <https://hub.docker.com/r/prom/prometheus/>`_.
   |

4. A **Node Exporter** server service will be deployed to all nodes in the swarm.

   | The Node Exporter server collects system metrics like cpu, memory and storage usage.
   | Prometheus will scrape the collected system metrics from all Node Exporters servers running in the swarm.
   | The Node Exporter server is a Docker Hub docker image provided by `Prometheus. <https://hub.docker.com/r/prom/node-exporter/>`_
   |

5. A **cAdvisor** server service will be deployed to all nodes in the swarm.

   | The cAdvisor server collects, aggregates, processes information on running docker containers.
   | Prometheus will scrape the collected metrics from all cAdvisor services running in the swarm.
   | The cAdvisor server is a Docker Hub docker image provided by `Google <https://hub.docker.com/r/google/cadvisor/>`_.
   |

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1   

