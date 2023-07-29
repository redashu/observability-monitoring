## We are watching don't worry  
<img src="images/logo.png" width=100>

---
# The Observation , Monitoring and alerting Engine 
<p> Prometheus is a free software application used for event monitoring and alerting. It records metrics in a time series database built using an HTTP pull model, with flexible queries and real-time alerting 
</p>

### General Info
<ol>
    <li> Open Source product </li>
    <li> Written in Golang  </li>
    <li> Originally Developed at SoundClound in 2012  </li>
    <li> Now CNCF is taking care  </li>
    <li> Prometheus is inspired by Google's Borgmon </li>

</ol>

## Prometheus Monitoring 

<img src="images/info.png">

<p>As Seen in above picture it can monitoring <b> Server | Network | Database | Applications | Batch jobs | Containers  </b>  and many more </p>
<br>
<hr>
### Metrics type supported  By prometheus 

```bash
Counter
Gauge
Histogram
Summary
```
<hr>
### Architecture and Components 

<img src="images/arch.png">

### Components 

### The Prometheus ecosystem consists of multiple components, many of which are optional:
<ol>
 <li>the main Prometheus server which scrapes and stores time series data </li>
<li>client libraries for instrumenting application code </li>
<li> a push gateway for supporting short-lived jobs</li>
<li> special-purpose exporters for services like HAProxy, StatsD, Graphite, etc.</li>
<li> an alertmanager to handle alerts</li>
<li> various support tools </li> 
</ol>

### Default configureation file 
---
Prometheus.yaml
---
```
global:
  scrape_interval:     15s
  evaluation_interval: 15s

rule_files:
  # - "first.rules"
  # - "second.rules"

scrape_configs:
  - job_name: prometheus
    static_configs:
      - targets: ['localhost:9090']
```

## By default promethes Export metrics  data of it's own server on  http://localhost:1122/metrics

<img src="images/metrics.png" width=600 height=400>

### checking version and other info 

<img src="images/status.png" width=600 height=400>



