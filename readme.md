# Running PetClinic on EKS

## Steps
1. Create an EKS cluster:
```
gcloud container clusters create petclinic   --zone us-central1-a   --num-nodes 3   --machine-type e2-small --disk-size 20
gcloud container clusters get-credentials petclinic --zone us-central1-a
```

2. Add and update the ingress-nginx repo:
```
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
```

3. Install nginx-ingress:
```
helm install nginx-ingress ingress-nginx/ingress-nginx
```

4. Add and update the jetstack repo:
```
helm repo add jetstack https://charts.jetstack.io
helm repo update
```

5. Install cert-manager:
```
helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --version v1.13.2 --set installCRDs=true
```

6. Argocd ip
```
https://35.193.35.159/
```
