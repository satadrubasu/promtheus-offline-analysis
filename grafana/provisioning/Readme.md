### Datasource COnfiguration Reference:  

1. Ensure the exact name of the datasource in the section:  

```
datasources  
- name: < should have the same name as from the exported dashboard>  
```

2. Ensure the port matches the port configured in the docker-compose.yml for the prometheus service  

```
# From the docker-compose.yml
services:
  prometheus:
  image: prom/prometheus
  ports:
    - 9090:9090
```

```
 # From the datasource.yml
 datasources:
   url: http://127.0.0.1:9090
```

3. Ensure the access is not proxy but direct.




