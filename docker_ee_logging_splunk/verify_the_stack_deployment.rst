..  _splunk_verify_the_stack_deployment:

Verify the Splunk stack deployment
==================================

Wait about a minute for the Splunk stack to be created.

1. Run the following **docker stack services** command on the swarm manager to display the stack services.

    .. code-block:: bash

        docker stack services splunk

    Example output:

    .. code-block:: text

        ID                  NAME                       MODE                REPLICAS            IMAGE                                     PORTS
        36cenosgqsgb        splunk_splunk-forwarder    global              2/2                 splunk/universalforwarder:7.0.0-monitor   *:1514->1514/tcp
        zawwlqz39hcq        splunk_splunk-enterprise   replicated          1/1                 splunk/splunk:7.0.0-monitor               *:8000->8000/tcp,*:8088->8088/tcp

2. Run the following **docker service ps** command on the swarm manager to display where the services are running and their statuses.

    .. code-block:: bash

        docker stack ps splunk

    Example output:

    .. code-block:: text

        ID                  NAME                                                IMAGE                                     NODE                DESIRED STATE       CURRENT STATE                ERROR               PORTS
        b6klp20dcd85        splunk_splunk-forwarder.a0fnl6bqvlvpih5u51fsqbk7i   splunk/universalforwarder:7.0.0-monitor   worker2             Running             Running about a minute ago
        u6n1t72f1mbc        splunk_splunk-forwarder.ucc6razv0ou0wi6i3x12pt1un   splunk/universalforwarder:7.0.0-monitor   worker1             Running             Running about a minute ago
        valqb6fpr1m9        splunk_splunk-enterprise.1                          splunk/splunk:7.0.0-monitor               manager             Running             Running about a minute ago

3. Run the following **docker service logs** commands on the swarm manager to display the logs for the services and check them for errors.

    .. code-block:: bash

        docker service logs splunk_splunk-enterprise

    .. code-block:: bash

        docker service logs splunk_splunk-forwarder

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
