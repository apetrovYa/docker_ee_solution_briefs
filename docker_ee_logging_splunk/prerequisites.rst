..  _splunk_pre-requisites:

Prerequisites
=============

Docker swarm
------------

A Docker swarm must be deployed and running.

* For a test environment a minimum of 3 nodes is required.
* For a production environment additional nodes should be deployed. 

Refer to `Docker Reference Architecture: Docker EE Best Practices and Design Considerations <https://success.docker.com/article/Docker_Reference_Architecture-_Docker_EE_Best_Practices_and_Design_Considerations>`_ for details.

jq command
----------

Some of the commands in this Solution Brief use the **jq** command to format and display json output.  If the **jq** command is not installed you can download and install it from here: https://github.com/stedolan/jq/wiki/Installation.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1