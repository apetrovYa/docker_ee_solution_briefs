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
        3w0isjfwib18        splunk_splunk-forwarder    global              3/3                 splunk/universalforwarder:7.0.0-monitor   *:1514->1514/tcp
        hm2i38qtvrvy        splunk_splunk-enterprise   replicated          1/1                 splunk/splunk:7.0.0-monitor               *:8000->8000/tcp,*:8088->8088/tcp

2. Run the following **docker service ps** command on the swarm manager to display where the services are running and their statuses.

    .. code-block:: bash

        docker stack ps splunk

    Example output:

    .. code-block:: text

        ID                  NAME                                                    IMAGE                                     NODE                DESIRED STATE       CURRENT STATE                ERROR                        PORTS
        eqfwf5j1xruv        splunk_splunk-forwarder.6dbmhj26ydctir5se6no0zewe       splunk/universalforwarder:7.0.0-monitor   worker3.acme.com    Running             Running about a minute ago
        os3gfyk1iu0h        splunk_splunk-forwarder.34usz92cx71n6nj2ahum95ojr       splunk/universalforwarder:7.0.0-monitor   worker2.acme.com    Running             Running about a minute ago
        prenu2lu25rs        splunk_splunk-forwarder.rdb0f9hgsi7533puaoi1mapln       splunk/universalforwarder:7.0.0-monitor   manager             Running             Running about a minute ago
        p57pol9bb6fi        splunk_splunk-enterprise.1                              splunk/splunk:7.0.0-monitor               worker1             Running             Running about a minute ago

3. Run the following **docker service logs** commands on the swarm manager to display the logs for the services and check them for errors.

    .. code-block:: bash

        docker service logs splunk_splunk-enterprise

    .. code-block:: bash

        docker service logs splunk_splunk-forwarder

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
