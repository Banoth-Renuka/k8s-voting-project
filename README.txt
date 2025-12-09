Kubernetes Voting App - manifests bundle

Images used (Docker Hub):
- voting app: dockersamples/examplevotingapp_vote:latest
- redis: redis:6-alpine
- worker: dockersamples/examplevotingapp_worker:latest
- postgres: postgres:14
- results app: dockersamples/examplevotingapp_result:latest

Apply order:
1. kubectl apply -f namespace.yml
2. kubectl apply -f secrets/postgres-secret.yml   (or use kubectl create secret ...)
3. kubectl apply -f pods/redis-pod.yml
4. kubectl apply -f services/redis-svc.yml
5. kubectl apply -f pods/postgres-pod.yml
6. kubectl apply -f services/postgres-svc.yml
7. kubectl apply -f pods/voting-app-pod.yml
8. kubectl apply -f services/voting-svc.yml
9. kubectl apply -f pods/worker-pod.yml
10. kubectl apply -f pods/results-app-pod.yml
11. kubectl apply -f services/results-svc.yml

Notes:
- Replace secret base64 values with secure values or create the secret with kubectl create secret generic.
- Replace images if you have different/private images.
- For production, use Deployments/StatefulSets, PVCs for Postgres, readiness/liveness probes, and resource requests/limits.
