..  _grafana_prometheus_monitoring_define_prometheus_as_data_source:

Define Prometheus as a data source
==================================

1. Click on the |add_data_source_button_icon| button to define Prometheus as a Data Source to Grafana.

    Example Screen:

    ..  image:: images/define_prometheus_as_data_source.png

    ..  |add_data_source_button_icon| image:: images/add_data_source_button_icon.png
        :width: 53 px
        :height: 43 px
        :align: bottom
        :alt: "Add data source"

2. Configure the Prometheus data source:

    * Specify a name for the Data Source in the **Name** field (e.g. Prometheus).
    * Select **Prometheus** for the Data Source type in the **Type** field. 
    * Specify the following URL in the **HTTP URL** field:

        .. code-block:: text

            http://monitoring_nginx:19090

        The hostname was specified in the docker_compose.yml file for the **monitoring_nginx** service.

        .. code-block:: yaml
            :emphasize-lines: 3

            monitoring_nginx:
                image: gforghetti/monitoring_nginx:latest
                hostname: monitoring_nginx

        The port must be **19090** which was configured in Nginx.

    * In the **Auth** section select the checkbox **Basic Auth**.
    * In the **Basic Auth Details** section specify the **prometheus** user and password which was previously configured.

    \
    
    Example Screen:

    ..  image:: images/save_and_test_prometheus_data_source.png

    ..  |save_and_test_data_source_button_icon| image:: images/save_and_test_data_source_button_icon.png
        :width: 65 px
        :height: 24 px
        :align: bottom
        :alt: "Save & Test"

    \

    Then click on the |save_and_test_data_source_button_icon| button.        

3. You should see a message saying **Data source is working**.

    Example Screen:

    ..  image:: images/create_prometheus_data_source.png

    ..  |create_data_source_back_button| image:: images/create_data_source_back_button.png
        :width: 46 px
        :height: 24 px
        :align: bottom
        :alt: "Back"

    \

    You can then click on the |create_data_source_back_button| button.

4. Data source is created.

    Example Screen:

    ..  image:: images/prometheus_data_source_created.png  

    ..  |grafana_dashboards_icon| image:: images/grafana_dashboards_icon.png
        :width: 24 px
        :height: 24 px
        :align: bottom
        :alt: "Dashboards"
    
    ..  |grafana_home_icon| image:: images/grafana_home_icon.png
        :width: 48 px
        :height: 64 px
        :align: bottom    
        :alt: "Home"

    \

    Then click on the |grafana_dashboards_icon| icon on the left frame, followed by clicking on the |grafana_home_icon| icon.

5. You should now be back at the Grafana **Home Dashboard**.

    Example Screen:

    ..  image:: images/grafana_home_dashboard.png

..  toctree::
    :hidden:
    :titlesonly:
    :maxdepth: 1  
       