# 1. Install Redash
helm upgrade --install -f my-values.yaml my-redash redash/redash

# 2. Redirect http to https
kubectl apply -f middleware.yml

# 3. Install cert-manager
#kubectl --validate=false apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.10.1/cert-manager.crds.yaml
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.10.1/cert-manager.yaml

# 4. Deployment of Ingress (traefik) with Let's Encrypt
kubectl apply -f my-ingress-prod.yml

# Check cedrtificate status
# kubectl describe certificates letsencrypt-prod

# Delete old certificate
# kubectl delete certificates letsencrypt-staging
