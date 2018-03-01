..  _elk_create_the_stack:

..  raw:: latex

    \newpage

Create the Elastic stack
========================

Run the following **docker stack deploy** command on the swarm manager to create the Elastic stack:

    ..  code-block:: bash

        docker stack deploy -c docker-compose.yml elk

Example output:

    .. code-block:: text

        Creating network elk_elk-backend
        Creating service elk_elastic-search
        Creating service elk_elastic-search2
        Creating service elk_logstash
        Creating service elk_kibana
   
..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
