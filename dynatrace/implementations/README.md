## How to Enable Log monitoring from oneagent 

```
[root@server ~]# /opt/dynatrace/oneagent/agent/tools/oneagentctl --get-app-log-content-access
false
[root@server ~]# /opt/dynatrace/oneagent/agent/tools/oneagentctl --get-app-log-content-access
false
[root@server ~]# /opt/dynatrace/oneagent/agent/tools/oneagentctl --set-app-log-content-access=true
Configuration changes were not applied, OneAgent service must be stopped first. You may use --restart-service to automate the process
[root@server ~]# /opt/dynatrace/oneagent/agent/tools/oneagentctl --set-app-log-content-access=true  --restart-service
Stopping OneAgent service

```

### after some time this will be like given below

```
root@server ~]# /opt/dynatrace/oneagent/agent/tools/oneagentctl --set-app-log-content-access=true  --restart-service
Stopping OneAgent service
Application logs access enabled successfully (LogAgent v.2.0)
Application logs access enabled successfully (LogAgent v.1.0)
Starting OneAgent service
[root@server ~]# 

```


