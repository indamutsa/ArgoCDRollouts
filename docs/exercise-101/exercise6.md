### Exercise 6: Installing Argo Rollouts

This exercise involves installing Argo Rollouts in order to begin configuring blue-green and canary deployments.
Argo Rollouts is a Kubernetes controller and set of CRDs which provide advanced deployment capabilities such as blue-green, canary, canary analysis, experimentation, and progressive delivery features to Kubernetes. It is essentially a kubernetes deployment manifest coupled with a CRD that allows you to configure the rollout strategy.

#### Install Argo Rollouts

```sh
# WORKSHOP_USER="<username>"
WORKSHOP_USER="indamutsa" # Setting the repository username to my username
argocd --port-forward --port-forward-namespace argocd login # Logging in to ArgoCD
argocd --port-forward-namespace argocd repo add "https://github.com/$WORKSHOP_USER/ArgoCDRollouts" # Adding the repository to ArgoCD
argocd --port-forward-namespace argocd app create argo-rollouts --repo "https://github.com/$WORKSHOP_USER/ArgoCDRollouts" --path manifests/ArgoCD101-RolloutsController --dest-namespace argo-rollouts --dest-server https://kubernetes.default.svc # Creating the rollout application by specifying the repository, path, destination namespace and server
argocd --port-forward-namespace argocd app sync argo-rollouts
```

You can now view the application at [https://localhost:8080/applications/argo-rollouts](https://localhost:8080/applications/argo-rollouts).
