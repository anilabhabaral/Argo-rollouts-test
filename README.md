# rollout-test

## Install ArgoRollouts into your Cluster
https://argoproj.github.io/argo-rollouts/installation/#controller-installation
```
kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml
```

## Install argo rollouts plugin for kubectl
https://argoproj.github.io/argo-rollouts/installation/#kubectl-plugin-installation
```
brew install argoproj/tap/kubectl-argo-rollouts
```

## Install a ingress controller for example nginx. If using minikube use below command:
```
minikube addons enable ingress
```

## Rollout Demo

1. Create the rollout, service and ingress
```
kubectl apply -f https://raw.githubusercontent.com/anilabhabaral/rollout-test/refs/heads/main/rollout.yaml
kubectl apply -f https://raw.githubusercontent.com/anilabhabaral/rollout-test/refs/heads/main/service.yaml
kubectl apply -f https://raw.githubusercontent.com/anilabhabaral/rollout-test/refs/heads/main/ingress.yaml
```

2. Watching rollouts

Via CLI:
```
kubectl argo rollouts get rollout rollouts-demo --watch
```

Dashboard:
```
kubectl argo rollouts dashboard
```

3. Rollout a new image

Change the image of the docker image you are using. Experiment with `blue`, `yellow`, `green`, `red`, etc.  
```
kubectl argo rollouts set image rollouts-demo \
  rollouts-demo=quay.io/rhn_support_abaral1/spring-test-rollout:2.0
```

4. Access the application using ingress:
```
curl rollout.test.com
```




# Reference
https://argoproj.github.io/argo-rollouts/getting-started/
