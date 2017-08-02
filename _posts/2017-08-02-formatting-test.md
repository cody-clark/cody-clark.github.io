### Creating the Redis Master Deployment
1. Launch a terminal window in the directory you downloaded the manifest files.
2. Apply the Redis Master Deployment from the `redis-master-deployment.yaml` file:

        kubectl apply -f redis-master-deployment.yaml

include code.html language="yaml" file="redis-master-deployment.yaml" ghlink="/docs/tutorials/docs/tutorials/stateless-application/redis-master-deployment.yaml"

{:start="3"}
3. Query the list of Pods to verify that the Redis Master Pod is running:

        kubectl get pods

   The response should be similar to this:

        NAME                            READY     STATUS    RESTARTS   AGE
        redis-master-1068406935-3lswp   1/1       Running   0          28s


4. Run the following command to view the logs from the Redis Master Pod:

**Note:** Replace POD-NAME with the name of your pod
{: .notice1}

        kubectl logs -f POD-NAME

   Ctrl + C

### Creating the Redis Master Service
The guestbook applications needs to communicate to the Redis master to write its data. You need to apply a [Service](https://kubernetes.io/docs/concepts/services-networking/service/) to proxy the traffic to the Redis master Pod.

1. Apply the Redis Master Service from the following `redis-master-service.yaml` file: 

        kubectl apply -f redis-master-service.yaml

include code.html language="yaml" file="redis-master-service.yaml" ghlink="/docs/tutorials/docs/tutorials/stateless-application/redis-master-service.yaml"

{:start="2"}
2. Query the list of Services to verify that the Redis Master Service is running:

        kubectl get service

   The response should be similar to this:

        NAME           CLUSTER-IP   EXTERNAL-IP   PORT(S)    AGE
        kubernetes     10.0.0.1     <none>        443/TCP    1m
        redis-master   10.0.0.151   <none>        6379/TCP   8s

## Start up the Redis Slaves
Although the Redis master is a single pod, you can make it highly available to meet traffic demands by adding replica Redis workers.

### Creating the Redis Slave Deployment
Deployments scale based off of the configurations set in the manifest file. In this case, the Deployment object specifies two replicas. 

If there are not any replicas running, this Deployment would start the two replicas on your container cluster. Conversely, if there are more than two replicas are running, it would scale down until two replicas are running. 

1. Apply the Redis Slave Deployment from the `redis-slave-deployment.yaml` file:

        kubectl apply -f redis-slave-deployment.yaml

include code.html language="yaml" file="redis-slave-deployment.yaml" ghlink="/docs/tutorials/docs/tutorials/stateless-application/redis-slave-deployment.yaml"

{:start="2"}
2. Query the list of Pods to verify that the Redis Slave Pods are running:

        kubectl get pods

   The response should be similar to this:

        NAME                            READY     STATUS              RESTARTS   AGE
        redis-master-1068406935-3lswp   1/1       Running             0          1m
        redis-slave-2005841000-fpvqc    0/1       ContainerCreating   0          6s
        redis-slave-2005841000-phfv9    0/1       ContainerCreating   0          6s

### Creating the Redis Slave Service
The guestbook application needs to communicate to Redis workers to read data. To make the Redis workers discoverable, you need to set up a Service. A Service provides transparent load balancing to a set of Pods.

1. Apply the Redis Slave Service from the following `redis-slave-service.yaml` file:

        kubectl apply -f redis-slave-service.yaml

include code.html language="yaml" file="redis-slave-service.yaml" ghlink="/docs/tutorials/docs/tutorials/stateless-application/redis-slave-service.yaml"

{:start="2"}
2. Query the list of Services to verify that the Redis Slave Service is running:

        kubectl get services

   The response should be similar to this:

        NAME           CLUSTER-IP   EXTERNAL-IP   PORT(S)    AGE
        kubernetes     10.0.0.1     <none>        443/TCP    2m
        redis-master   10.0.0.151   <none>        6379/TCP   1m
        redis-slave    10.0.0.223   <none>        6379/TCP   6s

## Set up and Expose the Guestbook Frontend
This tutorial uses a simple PHP server that is configured to talk to either the slave or master Services, depending on whether the client request is a read or a write. It exposes a simple JSON interface, and serves a jQuery-Ajax-based UX.

### Creating the Guestbook Frontend Deployment
1. Apply the frontend Deployment from the following `frontend-deployment.yaml` file:

        kubectl apply -f frontend-deployment.yaml

include code.html language="yaml" file="frontend-deployment.yaml" ghlink="/docs/tutorials/docs/tutorials/stateless-application/frontend-deployment.yaml"

{:start="2"}
2. Query the list of Pods to verify that the three frontend replicas are running:

        kubectl get pods -l app=guestbook -l tier=frontend

   The response should be similar to this:

        NAME                        READY     STATUS    RESTARTS   AGE
        frontend-3823415956-dsvc5   1/1       Running   0          54s
        frontend-3823415956-k22zn   1/1       Running   0          54s
        frontend-3823415956-w9gbt   1/1       Running   0          54s

### Creating the Frontend Service
The `redis-slave` and `redis-master` Services you applied are only accessible within the container cluster because the default type for a Service is [ClusterIP](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services---service-types). `ClusterIP` provides a single IP address for the set of Pods the Service is pointing to. This IP address is accessible only within the cluster.

If you want guests to be able to access your guestbook, you must configure the frontend Service to be externally visible, so a client can request the Service from outside the container cluster. Minikube can only expose Services through `NodePort`.  

**Note:** Some cloud providers, like Google Compute Engine or Google Container Engine, support external load balancers. If your cloud provider supports load balancers and you want to it, simply delete or comment out `type: NodePort`, and uncomment `type: LoadBalancer`. 
{: notice1}

1. Apply the frontend Service from the following `frontend-service.yaml` file:

        kubectl apply -f frontend-service.yaml
        
include code.html language="yaml" file="frontend-service.yaml" ghlink="/docs/tutorials/docs/tutorials/stateless-application/frontend-service.yaml"

{:start="2"}
2. Query the list of Services to verify that the frontend Service is running:

        kubectl get services 

   The response should be similar to this:

        NAME           CLUSTER-IP   EXTERNAL-IP   PORT(S)        AGE
        frontend       10.0.0.112   <nodes>       80:31323/TCP   6s
        kubernetes     10.0.0.1     <none>        443/TCP        4m
        redis-master   10.0.0.151   <none>        6379/TCP       2m
        redis-slave    10.0.0.223   <none>        6379/TCP       1m

### Viewing the Frontend Service via `NodePort`
Once the frontend Service is running, you need to find the IP address to view your Guestbook.

1. Run the following command to get the IP address for the frontend Service.

        minikube service frontend --url

   The response should be similar to this:

        http://192.168.99.100:31323

{:start="2"}
2. Copy the IP address, and load the page in your browser to view your guestbook.

### Viewing the Frontend Service via `LoadBalancer`
Once the frontend Service is running, you need to find the IP address to view your Guestbook.

1. Run the following command to get the IP address for the frontend Service.

        kubectl get service frontend

   The response should be similar to this:

        NAME       CLUSTER-IP      EXTERNAL-IP        PORT(S)        AGE
        frontend   10.51.242.136   109.197.92.229     80:32372/TCP   1m

{:start="2"}
2. Copy the External IP address, and load the page.

## Scale the Web Frontend 
Scaling up or down is easy because your servers are defined as a Service that uses a Deployment controller.

1. Run the following command to scale up the number of frontend Pods:

        kubectl scale deployment frontend --replicas=5

{:start="2"}
2. Query the list of Pods to verify the number of frontend Pods running:

        kubectl get pods

   The response should look similar to this: 

        NAME                            READY     STATUS    RESTARTS   AGE
        frontend-3823415956-70qj5       1/1       Running   0          5s
        frontend-3823415956-dsvc5       1/1       Running   0          54m
        frontend-3823415956-k22zn       1/1       Running   0          54m
        frontend-3823415956-w9gbt       1/1       Running   0          54m
        frontend-3823415956-x2pld       1/1       Running   0          5s
        redis-master-1068406935-3lswp   1/1       Running   0          56m
        redis-slave-2005841000-fpvqc    1/1       Running   0          55m
        redis-slave-2005841000-phfv9    1/1       Running   0          55m

3. Run the following command to scale down the number of frontend Pods:

        kubectl scale deployment frontend --replicas=2

4. Query the list of Pods to verify the number of frontend Pods running:

        kubectl get pods

   The response should look similar to this:

        NAME                            READY     STATUS    RESTARTS   AGE
        frontend-3823415956-k22zn       1/1       Running   0          1h
        frontend-3823415956-w9gbt       1/1       Running   0          1h
        redis-master-1068406935-3lswp   1/1       Running   0          1h
        redis-slave-2005841000-fpvqc    1/1       Running   0          1h
        redis-slave-2005841000-phfv9    1/1       Running   0          1h

Deleting the Deployments and Services also deletes any running Pods. Use labels to delete multiple resources with one command.

1. Run the following command to delete all Pods, Deployments, and Services.

        kubectl delete deployments,services -l "app in (redis, guestbook)"

   The response should be this:

        deployment "frontend" deleted
        deployment "redis-master" deleted
        deployment "redis-slave" deleted
        service "frontend" deleted
        service "redis-master" deleted
        service "redis-slave" deleted

2. Query the list of Pods to verify that no Pods are running:

        kubectl get pods
        
   The response should be this: 

        No resources found.

* Read more about [connecting applications](https://kubernetes.io/docs/concepts/services-networking/connect-applications-service/)
* Read more about [Managing Resources](https://kubernetes.io/docs/concepts/cluster-administration/manage-deployment/#using-labels-effectively)
