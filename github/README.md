# Encrypt token with below command
````
echo -n "<token>" | base64
````  
  
````update encrypted secret in secret file under notification-controller````
# Run Notification Controller in with flux 
````
kubectl apply -f github/
````
# Run kustomization files for checks with pod-status-check
````
kubectl apply -f kustomization.yml
````  
# Tell Flux to pull the manifests from Git and upgrade itself with:
````
flux reconcile source git flux-system
````    
