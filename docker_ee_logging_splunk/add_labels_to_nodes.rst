..  _splunk_add_labels_to_nodes:

Add labels to the Docker Nodes
==============================

Labels need to be added to the docker nodes in the swarm to match the labels defined in the :ref:`docker-compose.yml<splunk_download_docker_compose_yml>` file used to bring up the Splunk stack to ensure that:

* A single **Splunk Enterprise server** service runs on one node all by itself (cannot have a **Splunk Forwarder server** service running on the same node).

    * A label of ``splunk-node-type=enterprise-server`` needs to be added to one node in the swarm.

    \

    ..  note:: In a production environment more than 1 docker node should be assigned the label ``splunk-node-type=enterprise-server`` in order to provide a backup in case of a node failure. 
    
* A single **Splunk Forwarder server** service runs on each of the other nodes in the swarm.

    * A label of ``splunk-node-type=forwarder-server`` needs to be added to the remaining nodes in the swarm.

Follow the instructions below to add the labels to the nodes carefully.  Make sure you do not add both labels to any nodes!  

1. Run the following **docker node ls** command from a command prompt on the docker swarm manager to display the nodes in the swarm to get their **ID**.

    ..  code-block:: bash

        docker node ls

    Example output:

    .. code-block:: text

        ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS
        akh3ecyvt3y168gfjb2raxo7z     worker2.acme.com    Ready               Active
        gwkn7ydqvlzscvw1swfrxvhcs     worker1             Ready               Active
        kk1ncklruchfo5jpmoa7v4xhp *   manager             Ready               Active              Leader
   
2. Pick one node in the swarm and add a label to it so it will be chosen to run the **Splunk Enterprise server**.

    In this Solution Brief the docker swarm the manager node will be designated as the node where the single **Splunk Enterprise server** service will run. 
    In this example the **ID** of that node is ``kk1ncklruchfo5jpmoa7v4xhp``.

    Run the following **docker node update** command to add the label ``splunk-node-type=enterprise-server`` to the node with the **ID** ``kk1ncklruchfo5jpmoa7v4xhp``.

    ..  code-block:: bash

        docker node update --label-add 'splunk-node-type=enterprise-server' kk1ncklruchfo5jpmoa7v4xhp

3. Add a label to every other node in the swarm so they will be chosen to run a **Splunk Forwarder server** service.

    Run the command below to display the **IDs** of all nodes in the swarm, 
    filter out the node with **ID** ``kk1ncklruchfo5jpmoa7v4xhp``, and then add the label ``splunk-node-type=forwarder-server`` to the remaining nodes.

    ..  code-block:: bash

        for node in $(docker node ls -q | grep -v 'kk1ncklruchfo5jpmoa7v4xhp'); \
        do \
            docker node update $node --label-add 'splunk-node-type=forwarder-server'; \
        done

4. Run the following command to verify that the labels are correctly added:

    ..  code-block:: bash

        docker node ls -q | xargs docker node inspect | jq -r '.[].Spec.Labels' | grep 'splunk-node-type' | sort | awk '{print $2}'

    You should see one entry for **enterprise-server**, and as many entries for **enterprise-forwarder** as the number of remaining nodes in your swarm.

    Example output:

    ..  code-block:: text
        :emphasize-lines: 1

        "enterprise-server"
        "forwarder-server"
        "forwarder-server"      

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1