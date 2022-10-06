# deploy-shop-microservices

## Application to deploy : [https://github.com/GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo)
<br>

## Architecture 

![Image](/images/ms-shop-archi.png "Application architecture")

## Deployment strategy

What you need to know as a devops engineer to deploy a such architecture
- which service you need to deploy
- which service is talking to which service 
- how are the services communicating
- which databases are they using? 3rd party services?
- on which port does each service run
- which service is accessible from outside the cluste

![Image](/images/shop-archi.png "k8s components with ports")

### 1 - Create deployment and service files for each microservice

#### [See maninest files](https://github.com/hotiaDiallo/deploy-shop-microservices/blob/main/k8s-config/config.yaml)

This works but we can improve it with some Production and Security best practices

### 2 - Create deployment and service files for each microservice with Production and Security best practices
- Specify a pinned version on each container image
- Configure a liveness probe on each container
- Configure a readyness probe on each container
- Configure resource request for each container
- Configure resource limits for each container
- Use LoadBalancer to have only one entrypoint or ingress
- Configure more than one replica for high availability
- Use labels for your resources 
- Use namespaces to organize resources

#### [See the updated maninest files](https://github.com/hotiaDiallo/deploy-shop-microservices/blob/main/k8s-config/config.yaml)

This is good but we still have to improve it to avoid code repetition. If we look at our yaml files we alsmot have the same code : only some values are differentes. We can use helm charts. 

### 3 - Deploy using helm and helmfile

![Image](/images/check-deploy.png "Resources deployed")

<br>

http://139.144.160.109/80 (139.144.160.109 --> IP adresse of LoadBalancer on Linode)

![Image](/images/online-live.png "Online shop")



