### How to list all the indexes

```
 ELK git:(master) curl -XGET "http://localhost:9200/_cat/indices?v"

health status index                           uuid                   pri rep docs.count docs.deleted store.size pri.store.size
green  open   .geoip_databases                Ay6APRK9Q0GXG2BPEHuufA   1   0         43            0     40.1mb         40.1mb
green  open   .kibana-event-log-7.14.0-000001 Brdu-7dkQ5mvzFQ3s-ArKA   1   0          1            0      5.6kb          5.6kb
green  open   .kibana_7.14.0_001              XoVs09MrTISdGAyK1WMUDQ   1   0        118           23      2.2mb          2.2mb
green  open   .apm-custom-link                7aun2QueRVegbAYrDZ9iPQ   1   0          0            0       208b           208b
green  open   .apm-agent-configuration        I7FGmkIwTnGzoqFpWRjCZQ   1   0          0            0       208b           208b
green  open   kibana_sample_data_logs         6XJngLylT2an3H0-Fl132Q   1   0      14074            0      7.2mb          7.2mb
green  open   .kibana_task_manager_7.14.0_001 yIeZGoM_T6W_YEL0mwbFiw   1   0         14        26763      2.6mb          2.6mb
green  open   .async-search                   iX1iR_ATQCS4VePc67RJeQ   1   0          3            0     33.5kb         33.5kb
➜  ELK git:(master) 


```

### listing mappings / schema / columns of  indexes

```
 ELK git:(master) curl -XGET "http://15.207.1.202:9200/log_data/_mappings"                        

{"log_data":{"mappings":{"properties":{"log_level":{"type":"text","fields":{"keyword":{"type":"keyword","ignore_above":256}}},"message":{"type":"text","fields":{"keyword":{"type":"keyword","ignore_above":256}}},"source":{"type":"text","fields":{"keyword":{"type":"keyword","ignore_above":256}}},"timestamp":{"type":"date"}}}}}%        
```

