..  _splunk_test_collector_network_connection:

..  raw:: latex

    \newpage

Test the network connection
===========================

Test the network connection to the Splunk Enterprise Search Head server. From a Windows Powershell command prompt on the Docker Windows node issue the following command below. 
Substitute ``splunk-server`` below with the hostname or IP address of the Splunk Enteprise Search Head server.

    ..  code-block:: text

        Test-NetConnection -ComputerName "splunk-server" -P 8088 -InformationLevel Detailed

TCPTestSucceeded should be true.   

..  image:: images/test_network_connection.png             

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1
    