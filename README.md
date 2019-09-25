# Zeebe + Operate + Ingress Controller HELM Chart

This charts install:
- A Zeebe Cluster
- Operate configured to talk with the Zeebe Cluster
- Ingress Controller which
    - Expose Operate HTTP endpoint under `/`
    - If Kibana is enabled also expose Kibana HTTP endpoint under `/logs`
   

```
zeebe-cluster: 
  kibana:
    enabled: true     
    healthCheckPath: "/logs/app/kibana"
    ingress:
      enabled: true
      annotations:
        kubernetes.io/ingress.class: nginx
      path: /logs
      hosts:
        - ""
    extraEnvs:
      - name: SERVER_BASEPATH
        value: /logs
      - name: SERVER_REWRITEBASEPATH
        value: "true"
```