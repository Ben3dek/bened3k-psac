# PSAC-flux

1. Install flux

```sh
curl -s https://fluxcd.io/install.sh | sudo bash
```
2. configure kubectl

```sh
flux check --pre
```

3. generate github access token

https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens

then export it
```sh
export GITHUB_TOKEN=<your-token-here>
```
4. connect git
```sh
flux bootstrap github \
--token-auth \
--owner=<username> \
--repository=<repo> \
--path=<path-of-cluster-in-git> \
--personal
--branch main \
--namespace=<your-namespace>
```

Own
```sh
flux bootstrap github \
--token-auth \
--owner=Ben3dek \
--repository=bened3k-psac \
--path=./clusters/minikube \
--components-extra=image-reflector-controller,image-automation-controller \
--personal
--branch main
```

5. check if flux is running in the cluster
```sh
kubectl get pods -n <your-namespace>
```
6. Kustomize flex
