# Exposing gRPC microservices with HAProxy Ingress Controller on GKE

### Clone this repo and switch to branch "grpc_haproxy_controller".

```sh
git checkout grpc_haproxy_controller
```

### Create a new cluster

```sh
cd k8s_deployments/haproxy_controller
bash create_k8s_cluster.sh
```

### Deploy gRPC microservices with HAProxy Ingress Controller using automation script.

```sh
cd k8s_deployments/haproxy_controller
bash grpc_service_with_haproxy_controller_installation.sh
```

### Get HAProxy External LB IP Address  

```sh
kubectl get service haproxy-ingress -n ingress-controller
```

### Make entry in your local /etc/hosts file.  

```sh
# /etc/hosts
<ing_ip>	delivery.gship.com
```

### Check your PODs running in the Cluster. Access the Carrier PODs and make entry in /etc/hosts file to access the application via cli  

```sh
# Get carrier pods
kubectl get po -n kube-system | grep -i -e "carrier" 

# You have to make manual entry in /etc/hosts file
kubectl exec -it <pods> -n kube-system bash 
 
# /etc/hosts
<ing_ip>	delivery.gship.com
```

### Access the applicatin via CLI  

```sh
## to send request to carrier servie 
cd client_service && python carrier_cli_load_test.py 
```

### For more information and instructions follow the documentation.
