## Installing in no Self managed K8s 

## Note: 
<li> I am only considering Single Node of ElasticSearch </li>
<li> Changing Dynamic volume provising to Static </li>\
<li> Changing Healdess service to ClusterIP </li>

### Using helm to Install Elastic Search  new values.yaml

====> my-values.yaml 
```
replicas: 1
minimumMasterNodes: 1  
# ... (previous configuration)
# ... (previous configuration)

persistence:
  enabled: false  # Disable dynamic provisioning

volumeClaimTemplate:
  accessModes: ["ReadWriteOnce"]
  resources:
    requests:
      storage: 30Gi
  storageClassName: "static"  # Use the name of your static storage class
  ## Uncomment the following lines if you want to use a specific PV for each replica.
  # selector:
  #   matchLabels:
  #     volume-name: elasticsearch-data

staticPVs:
  - name: elasticsearch-data-0
    storage: 30Gi
    path: /path/on/host/0

# ... (remaining configuration)

# Define the StorageClass
storageClass:
  create: true
  name: "static"
  provisioner: "k8s.io/no-provisioner"  # No dynamic provisioning
  volumeBindingMode: "WaitForFirstConsumer"

# ... (remaining configuration)

service:
  enabled: false

```
