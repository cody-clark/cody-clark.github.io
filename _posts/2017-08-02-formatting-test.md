### Creating the Redis Master Deployment
1. Launch a terminal window in the directory you downloaded the manifest files.
2. Apply the Redis Master Deployment from the `redis-master-deployment.yaml` file:

        kubectl apply -f redis-master-deployment.yaml

{% include code.html language="yaml" file="redis-master-deployment.yaml" ghlink="/docs/tutorials/docs/tutorials/stateless-application/redis-master-deployment.yaml" %}

{:start="3"}
3. Query the list of Pods to verify that the Redis Master Pod is running:

        kubectl get pods

   The response should be similar to this:

        NAME                            READY     STATUS    RESTARTS   AGE
        redis-master-1068406935-3lswp   1/1       Running   0          28s

{:start="4"}
4. Run the following command to view the logs from the Redis Master Pod:

**Note:** Replace POD-NAME with the name of your pod
{: .note}

        kubectl logs -f POD-NAME
