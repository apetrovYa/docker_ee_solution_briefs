..  _splunk_configure_collector_conf:

..  raw:: latex

    \newpage

Configure the Collector
=======================

The Collector needs to be configured which includes:

1. Defining the Splunk Enterprise server :ref:`HTTP Event Collector connection <splunk_define_http_event_collector_conf>` to the Collector.
2. Defining the :ref:`Docker daemon installation directories <define_docker_daemon_installation_directories>` to the Collector.

..  _splunk_define_http_event_collector_conf:

Define HTTP Event Collector connection
--------------------------------------

1. Edit the file **collector.conf** (you can use notepad).

    .. code-block:: powershell

        notepad collector.conf

    **collector.conf** file opened for edit in notepad

    ..  image:: images/notepad_collector_conf.png

2. Look for the ``[output.splunk]`` section and configure the following parameters.

  | Uncomment the ``url =`` statement (remove semicolon) and substitute your Splunk enterprise server hostname in place of ``hec.example.com``. 
  | Uncomment the ``token =`` statement (remove semicolon) and substitute your Splunk enterprise server HTTP Event Collector Token in place of ``B5A79AAD-D822-46CC-80D1-819F80D7BFB0``. 
  | Uncomment the ``insecure =`` statement (remove semicolon) and set the value to ``true`` (to use the Splunk self-signed certificate).
  | Then save the file.
  |

    .. code-block:: text
        :emphasize-lines: 5,8,11

        # Splunk output
        [output.splunk]

        # Splunk HTTP Event Collector url
        url = https://hec.example.com:8088/services/collector/event/1.0

        # Splunk HTTP Event Collector Token
        token = B5A79AAD-D822-46CC-80D1-819F80D7BFB0

        # Allow invalid SSL server certificate
        insecure = true

3. Save the changes.          

..  _define_docker_daemon_installation_directories:

Define Docker daemon installation directories
---------------------------------------------

..  note:: If Docker was installed in the default location on the windows node, then these extra steps will not be necessary.

I installed Docker on the ``D`` drive in a directory named ``Docker``. It was then necessary for me to make additional updates to the **collector.conf** file. 
If Docker is installed in the default directories on the Docker Windows node, then these extra steps will not be necessary.

1. In the section ``[general.docker]`` I had to uncomment out (remove the semicolons) from the statements ``dockerRootFolder`` and ``path`` specify this:

    ..  code-block:: text
        :emphasize-lines: 4,13

        [general.docker]

        # path to docker root folder
        dockerRootFolder = D:\Docker\

        # Log files
        [input.files]

        # disable container logs monitoring
        ; disabled = false

        # root location of docker files
        path = D:\Docker\containers\
          
2. In the section ``[general.docker]`` I had to uncomment out (remove the semicolons) from the statements ``hardlinks`` and ``hardlinksPath`` and specify this:

    ..  code-block:: text
        :emphasize-lines: 4,5

        # read hardlinks instead of original files
        # on Windows that allows not to block the original directory, when
        # files are getting deleted by daemon
        hardlinks = true
        hardlinksPath = D:\Docker\containers\          

3. In the section ``[input.files::docker_service]`` I had to change the ``path`` and specify this:

    ..  code-block:: text
        :emphasize-lines: 7

        [input.files::docker_service]

        # disable host level logs
        ; disabled = false

        # root location of docker files
        path = D:\Docker\

4. Save the changes.            

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1


   
