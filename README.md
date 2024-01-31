# ArgoCD

 
We need to add the Helm repository of Argo CD to our local machine so that we can then deploy the particular chart using the following command:

    $ helm repo add argo https://argoproj.github.io/argo-helm
    $ kubectl create namespace argocd
    $ kubectl port-forward service/argocd-server -n argocd 9000:443
    $ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
    
    $ argocd login localhost:9000
    $ argocd app create nginx --repo https://charts.bitnami.com/bitnami --helm-chart nginx --revision 13.2.10 --dest-server https://kubernetes.default.svc --dest-namespace nginx

    $ argocd app list 
    $ argocd app sync nginx

### Install and run argocd manually via Kustomize
    $ kustomize build . | kubectl apply -f -
























