..  _splunk_windows_overview:

Solution Brief Overview
=======================

On 1/17/2018 `Splunk <https://www.splunk.com/>`_ announced `Docker Windows Containers Monitoring <https://splunkbase.splunk.com/app/3858/>`_ which features:

* Application logs with multiline support and enriched metadata from Windows Containers.
* Container and process metrics.
* Docker service logs collection.

There are 2 components that need to be installed in an existing Splunk deployment:

1. `Splunk Monitoring Windows Containers App <https://splunkbase.splunk.com/app/3858/>`_ that needs to be installed on the Splunk Search Head server.
2. `Collector <https://www.outcoldsolutions.com/docs/monitoring-wincontainers/>`_ (built and provided by `Outcold Solutions <https://www.outcoldsolutions.com/>`_) needs to be installed on all Docker Windows nodes.

This Solution Brief will only cover installing, configuring and using the `Splunk Monitoring Windows Containers App <https://splunkbase.splunk.com/app/3858/>`_ 
and the `Collector <https://www.outcoldsolutions.com/docs/monitoring-wincontainers/>`_.
You will need to have an up and running Splunk Enterprise Server Stack. 
Refer to the `Docker EE Logging using Splunk Enterprise Solution Brief <https://github.com/gforghetti/docker_ee_logging_splunk_solution_brief>`_ to deploy a Splunk Enterprise Server Stack.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
    