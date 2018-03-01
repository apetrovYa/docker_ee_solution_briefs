..  _elk_ensure_sufficient_memory:

..  raw:: latex

    \newpage

Ensure sufficient virtual memory
================================

Elasticsearch uses a mmapfs (memory mapped file system) directory by default to store its indices. The default operating system limits
on mmap counts is likely to be too low, which may result in out of memory exceptions.

On Linux, you can increase the limits by running the following command as root:

    ..  code-block::  bash

        sysctl -w vm.max_map_count=262144

The response should be:

    ..  code-block:: text

        vm.max_map_count = 262144

To set this value permanently, edit and update/add the **vm.max_map_count** setting in the **/etc/sysctl.conf** file on the docker node.

You will need to perform this configuration on all docker nodes where you will be deploying the Elasticsearch service on.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
   