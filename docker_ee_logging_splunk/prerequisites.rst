..  _splunk_pre-requisites:

Prerequisites
=============

Docker swarm
------------

To run this Solution Brief a Docker swarm must be deployed and running.

* For a test environment a minimum of 3 nodes is required.
* For a production environment additional nodes should be deployed. 

Refer to `Docker Reference Architecture: Docker EE Best Practices and Design Considerations <https://success.docker.com/article/Docker_Reference_Architecture-_Docker_EE_Best_Practices_and_Design_Considerations>`_ for details.

curl command
------------

Some of the commands in this Solution Brief use the **curl** command. If the **curl** command is not installed you can install it using the instructions below for the Linux distributions:

* Debian/Ubuntu

  ..  code-block:: bash

      apt-get update -qq;apt-get install curl -y

* CentOS/RHEL

  ..  code-block:: bash

      yum makecache fast;yum install curl -y

For other Linux distributions you can download and install it from here: https://curl.haxx.se/download.html.

jq command
----------

Some of the commands in this Solution Brief use the **jq** command to format and display json output.  If the **jq** command is not installed you can install it using the instructions below for the Linux distributions:

* Debian/Ubuntu

  ..  code-block:: bash

      apt-get update -qq;apt-get install jq -y

* CentOS/RHEL

  ..  code-block:: bash

      yum makecache fast;yum install jq -y

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1