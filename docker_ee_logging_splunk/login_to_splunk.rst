..  _splunk_login_to_splunk:

Login to Splunk
===============

Bring up a web browser and login to the Splunk Enterprise server. 

Substitute ``docker-node-name`` in the URL below with the hostname of any of the docker nodes running in the swarm.

    ``http://docker-node-name:8000``

You will be prompted for the Splunk user and password.

    * The default user id **admin**
    * The default password is **changeme**

You will have to change the **admin** password once logged in.

Example Screen:

..  image:: images/login_to_splunk.png

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1

    change_the_password   
    logged_in_to_splunk 
