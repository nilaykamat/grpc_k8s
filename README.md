# Exposing gRPC microservices with GLBC (GCE Ingress Controller) on GKE

### Clone this repo and switch to branch "grpc_gce_glbc".

```sh
git checkout grpc_gce_glbc
```

### Create a new cluster

```sh
cd k8s_deployments/
bash create_k8s_cluster.sh
```

### Deploy gRPC microservices with GLBC using automation script.

```sh
cd k8s_deployments/
bash grpc_with_glbc_installation.sh 
```

### Get Ingress IP Address  

```sh
kubectl get ing -o wide
```

### Run below command from the CLI to check from ingress IP Address.  

```sh
cd l7grpc/grpc_sample_service/
docker build -t l7grpc:latest .
docker run --add-host main.esodemoapp2.com:<IP_ADDRESS> -t l7grpc:latest /grpc_client --host main.esodemoapp2.com:443

Note: 
##Replace the IP address with your Ingress IP address
##Instead of using docker image “l7grpc:latest” use your own docker image or build from the source code. 

```
The requests are load balanced and served from different pods. 

### Run below command from the CLI to check from LB IP Address.  

```sh
cd l7grpc/grpc_sample_service/
docker build -t l7grpc:latest .
docker run --add-host main.esodemoapp2.com:<LB_IP_ADDRESS> -t l7grpc:latest /grpc_client --host main.esodemoapp2.com:443

Note: 
##Replace the IP address with your LB IP address
##Instead of using docker image “l7grpc:latest” use your own docker image or build from the source code. 

```
All the requests served from single pod only. 


### For more information and instructions follow the documentation.
