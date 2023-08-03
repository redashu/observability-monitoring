## We are watching don't worry  
---
### PromQL 

<pre>
  Prometheus PromQL (Prometheus Query Language) is a query language used to retrieve and manipulate time-series data from Prometheus
</pre>

<b> This is SQL like Language to fetch data using Query from Prometheus TSDB </b>

## Data types in PromQL  

### Info 
<pre>
Expression language data types
In Prometheus's expression language, an expression or sub-expression can evaluate to one of four types:
</pre>
<ul> 
<li> Instant vector - a set of time series containing a single sample for each time series, all sharing the same timestamp </li>  
<li> Range vector - a set of time series containing a range of data points over time for each time series </li> 
<li> Scalar - a simple numeric floating point value </li> 
<li> String - a simple string value; currently unused </li> 
</ul>

## Instant Vetctor 
<p> It is Going to have A single value as output for every query </p>

## Examples 

### Up 
<img src="images/iv1.png">

### prometheus_http_requests_total

<img src="images/pth.png">

## Range vector

<p> For Individual Query we can get Multiple values like shown below </p>

###  Examples 

## up[1m]

<img src="images/rgv1.png">

### node_cpu_seconds_total[1m]

<img src="images/rgv2.png">


## Matchers & Selectors 

### selectors 

```
=: Select labels that are exactly equal to the provided string.
!=: Select labels that are not equal to the provided string.
=~: Select labels that regex-match the provided string.
!~: Select labels that do not regex-match the provided string.
```

### Example query 

<img src="images/q1.png">

### Range Vector Time Division 

```
Time durations are specified as a number, followed immediately by one of the following units:

ms - milliseconds
s - seconds
m - minutes
h - hours
d - days - assuming a day has always 24h
w - weeks - assuming a week has always 7d
y - years - assuming a year has always 365d
```

