..  _splunk_volume_usage:

Volume usage
============

The Splunk services use the following volumes:

* **Persistent data** volumes

    * **/opt/splunk/etc**
    * **/opt/splunk/var**

* **Read-only** volumes for issuing docker commands (top, stats, event, inspect) and to access docker container information and logs in order to do the logging and monitoring.

    * **/var/lib/docker/containers**
    * **/var/run/docker.sock**
    * **/var/log**

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
   