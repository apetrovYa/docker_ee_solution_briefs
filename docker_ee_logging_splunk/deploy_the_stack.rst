..  _splunk_deploy_the_stack:

Deploy the Splunk stack
=======================

Run the following **docker stack deploy** command on the swarm manager to create the Splunk stack:

    .. code-block:: bash

        docker stack deploy -c docker-compose.yml splunk

Example output:

    .. code-block:: text

        Creating network splunk_splunk-frontend
        Creating network splunk_splunk-backend
        Creating service splunk_splunk-enterprise
        Creating service splunk_splunk-forwarder
   
..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1