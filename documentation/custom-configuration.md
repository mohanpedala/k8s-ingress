### Hide the Server-Header
* Create a file with below configuration or you can refer `ingress-configmap.yaml`

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

Reference [nginx-configuration configmap](https://kubernetes.github.io/ingress-nginx/user-guide/nginx-configuration/configmap/)
