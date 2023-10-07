## Installing in no Self managed K8s 

## Note: 
<li> I am only considering Single Node of ElasticSearch </li>
<li> Changing Dynamic volume provising to Static </li>
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

## Using helm  and kubectl 

### adding helm repo 
```
helm repo add elastic https://helm.elastic.co
```

### listing repo 

```
elasticsearch helm repo list
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /Users/humanfirmware/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /Users/humanfirmware/.kube/config
NAME                	URL                                               
prometheus-community	https://prometheus-community.github.io/helm-charts
stable              	https://charts.helm.sh/stable                     
elastic             	https://helm.elastic.co                           
➜  elasticsearch 

```

### Creating a namespace 

```
kubectl create ns elk
kubectl config set-context --current --namespace elk
```

### Installing elasticsearch

```
helm install elasticsearch elastic/elasticsearch -f my-values.yaml
```

### Verify 

```
 ELK helm ls
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /Users/humanfirmware/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /Users/humanfirmware/.kube/config
NAME            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                   APP VERSION
elasticsearch   elk             1               2023-10-07 11:48:45.450644 +0530 IST    deployed        elasticsearch-8.5.1     8.5.1      
➜  ELK 
```

###  Just wait for 2 minutes 

```
 ELK kubectl get po 
NAME                     READY   STATUS    RESTARTS   AGE
elasticsearch-master-0   1/1     Running   0          9m55s
➜  ELK 
➜  ELK kubectl get svc
NAME                            TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)             AGE
elasticsearch-master-headless   ClusterIP   None         <none>        9200/TCP,9300/TCP   9m58s
➜  ELK 
```
