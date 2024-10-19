# PSAC-flux

1. Install flux

curl -s https://fluxcd.io/install.sh | sudo bash

2. configure kubectl

flux check --pre

3. generate github access token

https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens

then export it
export GITHUB_TOKEN=<your-token-here>

4. connect git  
flux bootstrap github \
--token-auth \
--owner=<username> \
--repository=<repo> \
--path=<path-of-cluster-in-git> \
--personal
--branch main \
--namespace=<your-namespace>

flux bootstrap github \
--token-auth \
--owner=Ben3dek \
--repository=bened3k-psac \
--path=./clusters/minikube \
--personal
--branch main

5. check if flux is running in the cluster

kubectl get pods -n <your-namespace>

6. Kustomize flex
