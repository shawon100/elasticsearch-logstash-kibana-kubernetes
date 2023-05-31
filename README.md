# elasticsearch-logstash-kibana-kubernetes
Kubernetes Yamls and Helm values file for setting up ELK stack (Elasticsearch, Filebeat, Logstash, and Kibana) in Kubernetes Cluster

# Installation
1. Clone the repository

```
git clone https://github.com/shawon100/elasticsearch-logstash-kibana-kubernetes 
```

2. Then add the helm repo

```
helm repo add elastic https://helm.elastic.co
```
3. Create and Apply the persistent volumes for elastic search. 

```
kubectl apply –f pv.yaml
```
Then go to elasticsearch folder and install elasticsearch.

```
helm install elasticsearch elastic/elasticsearch --version="7.17.3" -f values.yaml
```

4. Create and Apply the persistent volumes for filebeat.

```
kubectl apply –f pv.yaml

```
Then Go to filebeat folder. Install filebeat 

```
helm install filebeat elastic/filebeat --version="7.17.3" -f values.yaml
```

5. Go to kibana folder, Install kibana using helm. 

```
helm install kibana  --version="7.17.3"  elastic/kibana

```
Then change the host name according to your host name in ingress file and apply the ingress.

```
kubectl apply –f .
```
6. Go to logstash folder and apply the yamls

```
kubectl apply –f .
```

7. Check the pods and If all pods are in the Running status then go to your kibana host address to access the ELK

