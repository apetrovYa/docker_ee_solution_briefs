..  _elk_disable_swapping:

..  raw:: latex

    \newpage

Disable swapping
================

Elasticsearch recommends disabling swapping when running in production as it is bad for performance.
There are three approaches to disabling swapping:

1. Disable all swap files.

    This is the preferred option.

2. Configure swappiness.

    This option is available on Linux systems. You need to ensure that the `sysctl <https://en.wikipedia.org/wiki/Sysctl>`_ value
    **vm.swappiness** is set to 1. This reduces the kernel’s tendency to swap and should not lead to
    swapping under normal circumstances, while still allowing the whole system to swap in emergency conditions.

3. Enable bootstrap.mem_lock.

    This option requires to you to use **mlockall** on Linux/Unix systems, or VirtualLock on Windows, to try
    to lock the process address space into `RAM <https://en.wikipedia.org/wiki/Random-access_memory>`_, preventing any Elasticsearch memory from being swapped out.

In this solution I will use option 3 - :ref:`Enable bootstrap.mem_lock <elk_enable_bootstrap_mem_lock>` to disable swapping for Elasticsearch.

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1      

    enable_bootstrap_mem_lock