# Running PetClinic on EKS

## Steps
1. Create an EKS cluster:
```
eksctl create cluster --name my-cluster --node-type t3.small --nodegroup-name my-nodes --nodes 2 --nodes-min 1 --nodes-max 3
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
