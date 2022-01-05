# Container Applications
Modern bespoke application development can be handled quite well as containers. The tooling available for local development and production deployment is becoming quite mature for kubernetes based environments.

## Rancher on K3s (for production linux vms)
From a basic ubuntu server (`20.04` recommended) you can setup [k3s](https://k3s.io/) and [rancher](https://rancher.com/docs/rancher/v2.6/en/installation/install-rancher-on-k8s/) as below:
```bash
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION=v1.21.8+k3s1 sh -s - --write-kubeconfig-mode 644 --kubelet-arg max-pods=254
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
kubectl config view --raw > ~/.kube/config; chmod 600 ~/.kube/config
helm repo add jetstack https://charts.jetstack.io
helm install cert-manager jetstack/cert-manager --namespace cert-manager --version v1.6.1 --set installCRDs=true --create-namespace
helm repo add rancher-stable https://releases.rancher.com/server-charts/stable
helm install rancher rancher-stable/rancher --namespace cattle-system  --version 2.6.3 --create-namespace --set hostname=localhost
```

## Rancher on Rancher Desktop (for development)
If you are running Windows, it's easier to use a packaged kubernetes environment like [Rancher Desktop](https://rancherdesktop.io/)
