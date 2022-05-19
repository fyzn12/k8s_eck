# k8s通过eck部署elk集群
> [ECK](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-quickstart.html) 部署k8s是比较推荐的  
  
## 流程  
> 1. Install custom resource definitions:  
> kubectl create -f https://download.elastic.co/downloads/eck/2.2.0/crds.yaml  
>   
> 2. Install the operator with its RBAC rules:  
> kubectl apply -f https://download.elastic.co/downloads/eck/2.2.0/operator.yaml
  
> 3. Monitor the operator logs:  
> kubectl -n elastic-system logs -f statefulset.apps/elastic-operator  
>    
> 4. 配置elasticsearch.yaml  
> kubectl apply -f Elasticsearch.yaml 

```  
    注意： 在配置过程中注意podTemplate的配置  
```  

> 5. 配置kibana.yaml  
> kubectl apply -f kibana.yaml 