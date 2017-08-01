### Creating the Redis Master Deployment
1. Launch a terminal window in the directory you downloaded the manifest files.
2. Apply the Redis Master Deployment from the `redis-master-deployment.yaml` file:

        kubectl apply -f redis-master-deployment.yaml

include code.html language="yaml" file="redis-master-deployment.yaml" ghlink="/docs/tutorials/docs/tutorials/stateless-application/redis-master-deployment.yaml"


3. Query the list of Pods to verify that the Redis Master Pod is running:

        kubectl get pods

   The response should be similar to this:

        NAME                            READY     STATUS    RESTARTS   AGE
        redis-master-1068406935-3lswp   1/1       Running   0          28s


4. Run the following command to view the logs from the Redis Master Pod:

**Note:** Replace POD-NAME with the name of your pod
{: .notice1}

        kubectl logs -f POD-NAME

### Creating the Redis Master Service
The guestbook applications needs to communicate to the Redis master to write its data. You need to apply a [Service](https://kubernetes.io/docs/concepts/services-networking/service/) to proxy the traffic to the Redis master Pod.

1. Apply the Redis Master Service from the following `redis-master-service.yaml` file: 

        kubectl apply -f redis-master-service.yaml

include code.html language="yaml" file="redis-master-service.yaml" ghlink="/docs/tutorials/docs/tutorials/stateless-application/redis-master-service.yaml"

2. Query the list of Services to verify that the Redis Master Service is running:

        kubectl get service

    The response should be similar to this:

        NAME           CLUSTER-IP   EXTERNAL-IP   PORT(S)    AGE
        kubernetes     10.0.0.1     <none>        443/TCP    1m
        redis-master   10.0.0.151   <none>        6379/TCP   8s

