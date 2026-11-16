## Monitoring Traces with Alloy, Tempo and Grafana


Below is the complete setup how to use Prometheus and Grafana to collect, store, query, and visualize numerical performance data (time-series metrics) from systems, containers, applications, cloud and infrastructures.  

To simplify the setup, I use docker images to monitor/visualize Prometheus container's metrics, Grafana container's metrics and host system metrics (using node-exporter).

**Setup**  
Run the below commands to download the demo repository and run Prometheus and Grafana.  
```bash
#Downloading the repository
git clone git@github.com:hiepdng/monitoring_metrics_with_prometheus_grafana.git

#Creating volumes
cd monitoring_traces_with_alloy_tempo_grafana
mkdir grafana_data
sudo chown -R 472:472 grafana_data
mkdir alloy_data
sudo chown -R 473:473 alloy_data
mkdir tempo_data
sudo chown -R 10001:10001 tempo_data

#Running containers
docker compose up -d
```
**Access Grafana web:**  
Go to http://localhost:3000/ to access your local Grafana webpage and view the host and containers metrics.  

To view specific container webpages:  
- Prometheus: http://localhost:9090/ or http://localhost:9090/metrics
- Node-exporter: http://localhost:9100/ or http://localhost:9100/metrics
- Grafana: http://localhost:3000/metrics  

**View Grafana Drilldown Metrics:**  
In the Grafana webpage (http://localhost:3000/), by default the Drilldown Metrics will display all metrics from Prometheus container, Grafana container and host system metrics. To filter and view only Prometheus metrics:  
 - Click filter and enter: `job = prometheus`.
 - Do similar for node_exporter or grafana: `job = node_exporter` or `job = grafana`

**Import pre-built Grafana dashboard:**  
Instead of building my own custom dashboard, I use a pre-built dashboard (ID = 1800) from https://grafana.com/grafana/dashboards/. This dashboard is for node-exporter (host computer) metrics.  
- Go to Grafana web http://localhost:3000/
- Click on **Dashboard** ->**new** ->**Import**
- Enter **1860** in the ID slot
- Click **Load** ->**Import**  
Now you can view all the plots that represent the metrics on the Grafana dashboard.  


