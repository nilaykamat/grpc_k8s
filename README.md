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

### Access the application at

```sh
https://delivery.gship.com/ui
```

### For more information and instructions follow the documentation.
