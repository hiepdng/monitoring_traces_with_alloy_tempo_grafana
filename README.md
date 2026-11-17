## Monitoring Traces with Alloy, Tempo and Grafana


Below is the complete setup how to use Grafana Alloy, Grafana Tempo and Grafana to creates a complete, end-to-end distributed tracing stack to monitor, collect, store, and visualize the journey of requests across microservices.   

To simplify the setup, I use docker images to demotrate traces.  

**Setup**  
Run the below commands to download the demo repository and run Alloy, Tempo and Grafana.  
```bash
#Downloading the repository
git clone git@github.com:hiepdng/monitoring_traces_with_alloy_tempo_grafana.git

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
- Alloy: http://localhost:12345
- Tempo: http://localhost:3200/ready or http://localhost:3200/metrics

**View Grafana Drilldown Traces:**  
To view traces page:  
- goto http://localhost:3000/
- Click on `Drilldown` ->`Traces`
- Make sure select Tempo as data source



