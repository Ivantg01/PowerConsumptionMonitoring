# PowerConsumptionMonitoring

This project is an example how to use Cloud and Virtualization technologies for system observability.

Integration of different tools to collect, process, store and display information regarding the power consumption of OLTs. An OLT is a Telecom equipment used to deliver fiber to the home services, such as internet, video or telephony.

## Tools
This project uses:
* Kafka to send and receive power consumption metrics in JSON format ![tools](https://skillicons.dev/icons?i=kafka) 
* Prometheus to store the collected information as time series ![tools](https://skillicons.dev/icons?i=prometheus)
* Grafana to build and display multiple dashboard ![tools](https://skillicons.dev/icons?i=grafana)
* Docker to run all components used ![tools](https://skillicons.dev/icons?i=docker)

## Folder structure:
* ```kafka```: bus to send and consume power consumption metrics
  * ```docker-compose-kafka-kraft-sasl.yml```: YAML used by docker compose to create the kafka container
  * ```kafka_server_jaas.conf```: Kafka configuration file for SASL credentials
  * ```sasl_server.properties```: Main Kafka-Kraft configuration file with SASL
 
* ```simulator```: metric generator
  * ```producer_sasl_energy.py```: Python program that emulates the generation of power consumption metrics from multiple elements
  * ```example.json```: example of a power consumption metric in JSON format

*  ```prometheus```: docker definitions for Prometheus and Grafana
  * ```docker_compose.yml```: YAML used by docker compose to create Prometeus and Grafana containers
  * ```prometheus.yml```: YAML used by Prometheus as its default configuration

* ```exporter```: program to 
  * power_exporter.py: Python program to implement the specific Prometheus exporter to collect metric to Kafka and export them to Prometheus
  * requirements.txt: file with the Python libs used by power_exporter.py, basically Kafka and Prometheus client libs.
  * dockerfile: file with the definition of the container for the Prometheus exporter used by Prometheus to collect metrics
  * docker_compose.yml: YAML used by docker to create the container of the Prometheus exporter.
   
## Grafana screenshots 
Grafana has been connected to Prometheus and different dashboards have been created: 

<img src="./screenshots/dashboard1.png" width="30%"></img>
<img src="./screenshots/dashboard2.png" width="30%"></img>
<img src="./screenshots/dashboard3.png" width="30%"></img>
<img src="./screenshots/dashboard4.png" width="30%"></img>
<img src="./screenshots/dashboard5.png" width="30%"></img>
<img src="./screenshots/dashboard6.png" width="30%"></img>



  
