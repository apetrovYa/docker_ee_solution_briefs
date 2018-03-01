..  _elk_installation_configuration:

Installation and Configuration
==============================

Prerequisite setup
------------------

In a production environment Elasticsearch recommends the following prerequisite setup be performed:

* :ref:`Disable swapping <elk_disable_swapping>`
* :ref:`Increase file descriptors <elk_increase_file_descriptors>`
* :ref:`Ensure sufficient virtual memory <elk_ensure_sufficient_memory>`
* :ref:`Ensure sufficient threads <elk_ensure_sufficient_threads>`

This prerequisite setup will be covered in this document. Refer to Elastic `Important System Configuration <https://www.elastic.co/guide/en/elasticsearch/reference/current/system-config.html>`_ for more details.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  

    disable_swapping
    increase_file_descriptors
    ensure_sufficient_memory
    ensure_sufficient_threads
