# GitOps using Flux and Flagger

## Prerequisites

- A Kubernetes Cluster
- A GitHub personal Access Token with repo permissions
- Flux

## Install the Flux CLI

Use the following command to install flux-cli in linux.

```bash
curl -S https://fluxcd.io/install.sh | sudo bash
```

## Export your credentials

Export your GitHub personal access token and username:

```bash
export GITHUB_TOKEN=<your-token>
export GITHUB_USER=<your-username>
```

## Check your Kubernetes cluster

Check you have everything needed to run Flux by running the following command:

```bash
flux check --pre
```

## Install Flux onto your cluster 

Run the following bootstrap command:

```bash
flux bootstrap github \
  --owner=<github-username> \
  --repository=<repo-name> \
  --branch=main \
  --path=./clusters/my-cluster \
  --personal
```

The above bootstrap command does the following:

- Creates a git repository ``` <repo-name> ``` on your GitHub Account.
- Adds Flux components manifests to the repository.
- Deploy Flux components to your Kubernetes Cluster.
- Configures Flux components to track the path ``` /clusters/my-cluster/ ``` in the repository.
