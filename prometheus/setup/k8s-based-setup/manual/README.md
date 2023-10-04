## To Deploy/install prometheus & grafana in any k8s cluster manually 

### using kubectl 

```
 manual git:(master) ✗ kubectl apply -f  yamls


configmap/prometheus-configmap unchanged
deployment.apps/prometheus-deployment unchanged
deployment.apps/grafana unchanged
service/ui-grafana configured
daemonset.apps/node-exporter unchanged
service/node-exporter-service unchanged
service/prom-server configured


➜  manual git:(master) ✗ 
```

### Verify 

```
  manual git:(master) ✗ kubectl  get  deploy
NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
grafana                 1/1     1            1           26m
prometheus-deployment   1/1     1            1           21h
➜  manual git:(master) ✗ 
➜  manual git:(master) ✗ kubectl  get  ds    
NAME            DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
node-exporter   2         2         2       2            2           <none>          22h
➜  manual git:(master) ✗ 
➜  manual git:(master) ✗ kubectl  get  cm 
NAME                   DATA   AGE
kube-root-ca.crt       1      23h
prometheus-configmap   1      22h
➜  manual git:(master) ✗ 
➜  manual git:(master) ✗ kubectl  get  svc
NAME                    TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
node-exporter-service   ClusterIP   10.102.245.125   <none>        9100/TCP         22h
prom-server             NodePort    10.111.90.131    <none>        9090:32420/TCP   23h
ui-grafana              NodePort    10.105.184.142   <none>        3000:32409/TCP   25m
➜  manual git:(master) ✗ 
```

