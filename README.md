# master  
* 安装   
> helm install elasticsearch-master elastic/elasticsearch --version 7.12.1 -n elk -f es-master-values.yaml  
>   
  
* 卸载  
> helm uninstall elasticsearch-master -n elk  
>   
# data  

* 安装
> helm install elasticsearch-data elastic/elasticsearch --version 7.12.1 -n elk -f es-data-values.yaml
>

* 卸载
> helm uninstall elasticsearch-data -n elk    
>
  
# client  

* 安装
> helm install elasticsearch-client elastic/elasticsearch --version 7.12.1 -n elk -f es-client-values.yaml
>

* 卸载
> helm uninstall elasticsearch-client -n elk
>
> 
# 创建Ingress-controller
  
> helm install nginx-ingress ingress-nginx/ingress-nginx \
--version 4.0.13 \
--namespace ingress-basic --create-namespace \
--set controller.replicaCount=3 \
--set controller.nodeSelector."kubernetes\.io/os"=linux \
--set controller.image.registry=$ACR_URL \
--set controller.image.image=$CONTROLLER_IMAGE \
--set controller.image.tag=$CONTROLLER_TAG \
--set controller.image.digest="" \
--set controller.admissionWebhooks.patch.nodeSelector."kubernetes\.io/os"=linux \
--set controller.admissionWebhooks.patch.image.registry=$ACR_URL \
--set controller.admissionWebhooks.patch.image.image=$PATCH_IMAGE \
--set controller.admissionWebhooks.patch.image.tag=$PATCH_TAG \
--set controller.admissionWebhooks.patch.image.digest="" \
--set defaultBackend.nodeSelector."kubernetes\.io/os"=linux \
--set defaultBackend.image.registry=$ACR_URL \
--set defaultBackend.image.image=$DEFAULTBACKEND_IMAGE \
--set defaultBackend.image.tag=$DEFAULTBACKEND_TAG \
--set defaultBackend.image.digest=""