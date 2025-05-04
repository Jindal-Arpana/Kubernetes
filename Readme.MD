Commands to create the configMap, services and webApp in Kubernetes

            PS C:\Users\arpanaji\kube_hands_on> kubectl apply -f .\mongo-config.yaml
            configmap/mongo-config created

            PS C:\Users\arpanaji\kube_hands_on> kubectl apply -f .\mongo-app.yaml
            deployment.apps/mongo-deployment created
            service/mongo-service created

            PS C:\Users\arpanaji\kube_hands_on> kubectl apply -f .\web-app.yaml
            deployment.apps/webapp-deployment created
            service/webapp-service created

            PS C:\Users\arpanaji\kube_hands_on> kubectl get pods
            NAME                                READY   STATUS                       RESTARTS   AGE
            mongo-deployment-6d5b7d8bdc-c8qsv   0/1     CreateContainerConfigError   0          18s
            webapp-deployment-cf8d68b5b-pr52g   0/1     CreateContainerConfigError   0          10s

            PS C:\Users\arpanaji\kube_hands_on> kubectl get pods -o wide
            NAME                                READY   STATUS                       RESTARTS   AGE   IP            NODE       NOMINATED NODE   READINESS GATES
            mongo-deployment-6d5b7d8bdc-c8qsv   0/1     CreateContainerConfigError   0          23s   10.244.0.9    minikube   <none>           <none>
            webapp-deployment-cf8d68b5b-pr52g   0/1     CreateContainerConfigError   0          15s   10.244.0.10   minikube   <none>           <none>

            PS C:\Users\arpanaji\kube_hands_on> minikube ip
            192.168.155.189

            PS C:\Users\arpanaji\kube_hands_on> kubectl get svc
            NAME             TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
            kubernetes       ClusterIP   10.96.0.1       <none>        443/TCP          8m41s
            mongo-service    ClusterIP   10.98.61.255    <none>        27017/TCP        2m44s
            webapp-service   NodePort    10.104.170.23   <none>        8081:30100/TCP   2m36s

            PS C:\Users\arpanaji\kube_hands_on> minikube service webapp-service
            |-----------|----------------|-------------|------------------------------|
            | NAMESPACE |      NAME      | TARGET PORT |             URL              |
            |-----------|----------------|-------------|------------------------------|
            | default   | webapp-service |        8081 | http://192.168.155.189:30100 |
            |-----------|----------------|-------------|------------------------------|

Commands to delete and flush the create files in Kubernetes

            PS C:\Users\arpanaji\kube_hands_on> kubectl delete deployment --all
            deployment.apps "mongo-deployment" deleted
            deployment.apps "webapp-deployment" deleted

            PS C:\Users\arpanaji\kube_hands_on> kubectl delete service --all   
            service "kubernetes" deleted
            service "mongo-service" deleted
            service "webapp-service" deleted

            PS C:\Users\arpanaji\kube_hands_on> kubectl delete secret --all 
            secret "mongo-secret" deleted

            PS C:\Users\arpanaji\kube_hands_on> kubectl delete configmap --all
            configmap "kube-root-ca.crt" deleted
            configmap "mongo-config" deleted

