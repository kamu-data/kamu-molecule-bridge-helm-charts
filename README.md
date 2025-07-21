# Kamu-Molecule Bridge Helm Chart
This repo hosts the Helm chart for deploying [`kamu-molecule-bridge`](https://github.com/kamu-data/kamu-molecule-bridge) component into Kubernetes cluster.

To use the chart you will need to point helm at this chart repository like so:

```sh
helm repo add kamu-molecule-bridge \
  https://kamu-data.github.io/kamu-molecule-bridge-helm-charts/

helm repo update

helm install <release-name> \
  kamu-molecule-bridge/kamu-molecule-bridge \
  [--version <version>] \
  [--values values.yaml]
```


## Updating and Publishing
To publish the Helm chart artifacts this repo is using `gh-pages` (*a mechanism through which the contents of `gh-pages` branch in GitHub can be served as a static website*).

The Helm repository index is located [here](https://kamu-data.github.io/kamu-molecule-bridge-helm-charts/).

A routine release procedule of the new application image looks like this:
1. Update `appVersion` in the `Chart.yaml` to desired application version (same as OCI image tag)
2. Increment `version` in `Chart.yaml` - this is the version of the chart itself and must be incremented with every change in order to publish the updates
3. Commit and push your changes to `master`
4. The automated CI action will detect the changes in the chart, build the artifacts, tag the new release, and publish the updated chart index file via `gh-pages`
