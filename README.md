# aks-crossplane
This is a repository for trying different crossplane techniques to provision infrastructure to the cloud.

## setup

  ### pre-requisites:
  - Kubernetes cluster for deploying to (typically local micro distro, e.g. K3D, Minikube, KIND)
  - Azure account and az cli tool

  ### generate credentials.json file:
  ```
  az login
  az ad sp create-for-rbac --sdk-auth --role Owner --scopes /subscriptions/<Subscription_ID>
  ```

  ### live docs:
  - see [here](https://marketplace.upbound.io/providers/upbound/provider-azure/v0.29.0) for full setup

## run
  `kubectl apply -R -f packages/dosky/`
  `kubectl apply -f claim/<desired_claim.yaml>`

## monitoring resource status:

`watch kubectl get composition,Dosky,xrd,XDosky,ResourceGroup,provider,providerConfig.azure`