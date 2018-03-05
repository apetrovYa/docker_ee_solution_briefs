..  _splunk_generate_logging_data:

Generate logging data
=====================

Run the following **curl** command to cause the Apache HTTP Web Server container to generate logging data. Substitute ``docker-node-name`` with the hostname of
any docker node in the swarm.

    .. code-block:: bash

        curl docker-node-name:80
     
    Example output:
     
    .. code-block:: text

        <html><body><h1>It works!</h1></body></html>

Run the following **curl** command to cause the Apache HTTP Web Server container to generate logging data. Substitute ``docker-node-name`` with the hostname of
any docker node in the swarm.

    .. code-block:: bash

        curl docker-node-name:80/invalid
     
    Example output:
     
    .. code-block:: text

        <!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
        <html><head>
        <title>404 Not Found</title>
        </head><body>
        <h1>Not Found</h1>
        <p>The requested        

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1