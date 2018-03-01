.. _elk_volume_usage:

Volume usage
============

1. The Elasticsearch service stores it's persistent data on a volume.

   In this solution brief a cluster of 2 Elasticsearch services are being deployed, each service requires their own volume.  

     * **/usr/share/elasticsearch/data**

2. The Logstash service stores it's persistent pipeline data on a volume.

     * **/usr/share/logstash/pipeline/**

.. toctree::
   :titlesonly:
   :hidden:
   :maxdepth: 4
   