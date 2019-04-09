### Hide the Server-Header
* Create a file with below configuration or you can refer [ingress-configmap.yaml](../ingress-configmap.yaml)

  ```yaml
  kind: ConfigMap
  apiVersion: v1
  metadata:
    name: nginx-configuration
    namespace: ingress-nginx
    labels:
      app: ingress-nginx
  data:
     server-tokens: "False"
  ```
* Apply the configuration
  ```bash
  $ kubectl apply -f ingress-configmap.yaml
  ```
* Verify configuration -->
  - look for `# Custom code snippet configured in the configuration configmap` and `server_tokens`

  ```bash
  $ kubectl exec -it <pod_name> -n ingress-nginx cat /etc/nginx/nginx.conf
  ```
  - To know the ingress-controller pod name for the above command.
    ```bash
    $ kubectl get pods -n ingress-nginx
    ```
* To verify if the ConfigMap is created use the below command (optional).
  ```bash
  $ kubectl get configmaps -n ingress-nginx

  # Output
  NAME                              DATA      AGE
  ingress-controller-leader-nginx   0         23h
  nginx-configuration               2         23h
  tcp-services                      0         23h
  udp-services                      0         23h
  ```

Reference [nginx-configuration configmap](https://kubernetes.github.io/ingress-nginx/user-guide/nginx-configuration/configmap/)
