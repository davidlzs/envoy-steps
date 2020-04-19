## Serice Mesh with Istio
0. Build application docker images
    ```bash
    bash build_images.sh
    ```
1. Add `istio-inejction=enabled` label to default namespace, to make Istio automatically inject th sidecar proxy (`istio-proxy` and `istio-init`)
    ```bash
    kubectl label namespace default istio-injection=enabled
    ```
2. Deploy applications to Kubernetes cluster
    ```bash
    kubectl apply -f service_a_b_c.yaml
    ```
3. Create ingress gateway
    ```bash
    kubectl apply -f service_a_b_c_gatewy.yaml
    ```
 4. Testing
    * Set `INGRESS_PORT`
        ```bash
        export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].nodePort}')
        ```
    * Set `INGRESS_PORT` (minikube)
        ```bash
        export INGRESS_HOST=$(minikube ip)
        ```
    * Set `GATEWAY_URL`
        ```bash
        export 
        GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT
        ```
    * Request service_a api:
        ```bash
        curl -v http://$GATEWAY_URL/
        ```