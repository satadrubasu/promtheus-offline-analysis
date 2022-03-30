## 1) Local Machine Setup

a) Docker should be installed  
  > docker info  

b) docker-compose should be installed  
  > docker-compose info  

Verify:  
> docker netowrk ls
> docker volume ls
> docker volume prune ( removed unwanted volumes )

## 2) Download the offline dump for prometheus you want to load the data from.  
 ```  
  i) Unzip and extract to a temp location  
 ```

## 3) Working DIrectory for this project  
  1. Checkput this project and be at folder which contains the docker-compose.yl fo executing all docker compose commands.  
  2. update the .env file ( hidden) with two params 

  ```
  PROM_SNAPSHOT_LOC --> Path of the extracted folder containing the prom export snapshot
  RETENTION_DAYS --> Should be at least the number of days we need to go back in time from current date which has the 
  ```
## 4) Validate the docker-compose.yml

Go to the project folder location with the docker-compose.yml file.  
> docker-compose config

## 5) Run the docker compose

1. Run the docker compose in detached mode  
  ```
  docker-compose up -d
  docker ps -a
  ```

2. To bring down the containers:  
  ```
  docker-compose down
  ( from the location of the docker-compose.yml )
 ```

## 6) Configuring Datasource ( Provisioning via docker compose ) 
  1. When we import grafana dashboard jsons for offline analysis, we need to ensure the datasource to be configured has the same name as in imported json. e.g PCF : " Prometheus-ds"  
  The datasource configuration is also automated and provisioned via configuration in the following file:  
  > grafana/provisioning/datasources/datasource.yml  

## 7) Configuring Dashboard 
 1. Place all the dashboard json files to be auto imported at the following location :  

  > grafana/provisioning/dashboards  



## Maintenance over time : 
 1. Remove all docker volumes:  
  ```
  docker volume prune
  docker volume ls
  docker volume inspect
  ```
 

  
