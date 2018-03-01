..  _elk_install_license:

Install Elastic License
========================

In order to secure the Elastic stack using the Elastic X-Pack package included with the Elastic docker images, you will need to obtain a license other than the Basic Free License.
The Basic Free license does not even allow you to secure the Kibana console. Anyone will be able to login without being prompted for credentials.

Go to `Elastic Subscriptions <https://www.elastic.co/subscriptions>`_ for more details. 

Install Elastic License
----------------------- 

You can execute the following **curl** command on any docker node in the swarm to install your Elasticsearch license. 
Substitute ``elastic_license.json`` below with your Elastic license file. 
You will be prompted for the Elastic password which was specified in the :ref:`docker-compose.yml<elk_docker_compose_yml>` file in the environment for the Elasticsearch service.

    ..  code-block:: bash

        curl -XPUT -u elastic 'http://127.0.0.1:9200/_xpack/license' -H "Content-Type: application/json" -d @elastic_license.json

    ..  code-block:: text

        Enter host password for user 'elastic':

    Example output:

    ..  code-block:: json

        {"acknowledged":true,"license_status":"valid"}        

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  