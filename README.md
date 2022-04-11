# notifications_to_git

# Install Minikube Cluster
  [minikube_setup](https://github.com/Naresh240/kubernetes/blob/main/minikube-setup/README.md)
# Installing flux
````
  wget https://github.com/fluxcd/flux2/releases/download/v0.27.4/flux_0.27.4_linux_amd64.tar.gz 
  tar xvf flux_0.27.4_linux_amd64.tar.gz
  mv flux /usr/bin
````
# Create github token
````
  export GITHUB_TOKEN="provide github token"
````  
# Flux Bootstraping
````
  export GITHUB_USER="naresh240"
  export GITHUB_REPO="flux-notification-controller"
  export GITHUB_BRANCH="master"
  export GITHUB_DIR="./clusters"
  
  flux bootstrap github \
      --owner=$GITHUB_USER \
      --repository=$GITHUB_REPO \  
      --branch=$GITHUB_BRANCH \
      --path=$GITHUB_DIR \
      --token $GITHUB_TOKEN
````      
# Encrypt token with below command
````
  echo -n "<token>" | base64
````  
  
````update encrypted secret in secret file under notification-controller````
# Run Notification Controller in with flux 
````
  kubectl apply -f notification-controller/
````
# Run kustomization files for checks with pod-status-check
````
  kubectl apply -f kustomization.yml
````  
# Tell Flux to pull the manifests from Git and upgrade itself with:
````
    flux reconcile source git flux-system
````    
