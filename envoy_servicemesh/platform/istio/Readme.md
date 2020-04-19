## Serice Mesh with Envoy
0. Build application docker images
```bash
bash build_images.sh
```
1. Add `istio-inejction=enabled` label to default namespace
```bash
kubectl label namespace default istio-injection=enabled
```
2. Deploy applications to Kubernetes cluster
```bash
kubectl apply -f service_a_b_c.yaml
```
3. Create ingress gateway

4. Testing
