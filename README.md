# Exposing gRPC microservices with Nginx Ingress Controller on GKE

### Clone this repo and switch to branch "grpc_nginx_controller".

```sh
git checkout grpc_nginx_controller
```

### Create a new cluster

```sh
cd k8s_deployments/nginx_controller/
bash create_k8s_cluster.sh
```

### Deploy gRPC microservices with Nginx Ingress Controller using automation script.

```sh
cd k8s_deployments/nginx_controller/
bash grpc_service_with_nginx_controller_installation.sh
```

### Get Ingress IP 

```sh
kubectl get ing -o wide --all-namespaces
```

### Make entry in /etc/hosts file to access the application via browser and cli  

```sh
# /etc/hosts
<ing_ip>	delivery.gship.com
```

### Access the applicatin via CLI  

```sh
## to send request to carrier servie 
cd client_service && python carrier_cli_load_test.py 

## to send request to shipment servie 
cd client_service && python shipment_cli_load_test.py
```

### Access the application on broser

```sh
https://delivery.gship.com/ui
```

### For more information and instructions follow the documentation.
