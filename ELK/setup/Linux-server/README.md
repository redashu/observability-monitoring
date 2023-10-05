## Steps to Install on Linux Server

### Installing java

```
sudo yum install java-1.8.0-openjdk

```

### Creating yum repo 

```
sudo tee /etc/yum.repos.d/elasticsearch.repo <<EOF
[elasticsearch-7.x]
name=Elasticsearch repository for 7.x packages
baseurl=https://artifacts.elastic.co/packages/7.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md
EOF

```

### Importing key

```
sudo rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch
```

### Installing ElasticSearch 

```
sudo yum install elasticsearch

```

### Above step may give you output like this 

```
 Installing : elasticsearch-8.10.2-1.x86_64                                                                                       1/1 
--------------------------- Security autoconfiguration information ------------------------------

Authentication and authorization are enabled.
TLS for the transport and HTTP layers is enabled and configured.

The generated password for the elastic built-in superuser is : XvZsEeXtP5GyxKHoaZra

If this node should join an existing cluster, you can reconfigure this with
'/usr/share/elasticsearch/bin/elasticsearch-reconfigure-node --enrollment-token <token-here>'
after creating an enrollment token on your existing cluster.

You can complete the following actions at any time:

Reset the password of the elastic built-in superuser with 
'/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic'.

Generate an enrollment token for Kibana instances with 
 '/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana'.

Generate an enrollment token for Elasticsearch nodes with 
'/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node'.

-------------------------------------------------------------------------------------------------
### NOT starting on installation, please execute the following statements to configure elasticsearch service to start automatically using systemd
 sudo systemctl daemon-reload
 sudo systemctl enable elasticsearch.service
### You can start elasticsearch service by executing
 sudo systemctl start elasticsearch.service
  Verifying  : elasticsearch-8.10.2-1.x86_64                                                                                       1/1 

Installed:
  elasticsearch.x86_64 0:8.10.2-1                                                                                                      

Complete!

```

