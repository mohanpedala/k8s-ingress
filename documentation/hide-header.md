### Hide the Server-Header
* Add the below ConfigMap to `mandatory.yml`
  ```
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
