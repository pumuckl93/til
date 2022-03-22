---
title: How to use a helm chart locally
permalink: how-to-use-a-helm-chart-locally
date: 2022-03-22T15:31:24+01:00
tags: Kubernetes Helm DevOps
---

# Running Helm

Helm is a way to bundle your kubernetes deployments. Most of the time you will
use existing helm charts and pull them for a remote repo. However in some case a
helm chart might not be published or you wanna tweak it by yourself in that case
you can deploy it from a local directory.

# Running Helm from a local directory

- Clone the repo of your desired helm chart
- Check if there are any dependencies in the `Chart.yaml`
- Add dependencies repos via `helm repo add`
- Build `helm dep build ./charts/<package>` this will place the dependencies as
  zipped files in the charts subfolder
- `helm upgrade --install ./charts/<package`
