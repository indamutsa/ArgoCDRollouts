### Exercise 2: Using the Argo CD CLI

In this exercise we will deploy our first application using Argo CD CLI.

#### Set up a simple test application

Replace `<username>` with your GitHub username in the first command below.

```sh
# WORKSHOP_USER="<username>"
WORKSHOP_USER="indamutsa" # Setting the repository username to my username
argocd --port-forward --port-forward-namespace argocd login # Logging in to ArgoCD
argocd --port-forward-namespace argocd repo add "https://github.com/$WORKSHOP_USER/ArgoCDRollouts" # Adding the repository to ArgoCD
argocd --port-forward-namespace argocd app create guestbook --repo "https://github.com/$WORKSHOP_USER/ArgoCDRollouts" --path manifests/ArgoCD101-GuestbookManifests --dest-namespace default --dest-server https://kubernetes.default.svc # Creating the application by specifying the repository, path, destination namespace and server
argocd --port-forward-namespace argocd app sync guestbook # Syncing the application
```

Verify the test application by going to the Argo CD UI.

To programmatically delete the resources you've created using ArgoCD, you can use ArgoCD CLI commands similar to how you created them.

- `Delete the Application`: This will delete the `guestbook` application but not its underlying resources in Kubernetes.

```bash
argocd --port-forward-namespace argocd app delete guestbook
```

- `Delete the Repository`: If you added a repository, you can remove it too.

```bash
argocd --port-forward-namespace argocd repo rm "https://github.com/$WORKSHOP_USER/ArgoCDRollouts"
```

> Note: If you have multiple repositories, you can list them using `argocd --port-forward-namespace argocd repo list`
