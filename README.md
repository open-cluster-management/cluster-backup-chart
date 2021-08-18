# cluster-backup-chart
Open Cluster Management cluster backup Helm chart

------

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Community, discussion, contribution, and support](#community-discussion-contribution-and-support)
- [Getting Started](#getting-started)
- [Prerequisite Tools](#prerequisite-tools)
- [Building for Development](#building-for-development)
- [Testing on an existing OKD cluster with OCM](#testing-on-an-existing-okd-cluster-with-ocm)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

------

## Community, discussion, contribution, and support

Check the [CONTRIBUTING Doc](CONTRIBUTING.md) for how to contribute to the repo.

## Getting Started
Cluster backup chart is a helm chart used for deploying the [Cluster backup operator](https://github.com/open-cluster-management/cluster-backup-operator). This is a guide on how to build and run open-cluster-management cluster-backup-chart.

## Prerequisite Tools

- [helm](https://helm.sh/docs/intro/install/)

## Building for Development
<pre>
git clone https://github.com/open-cluster-management/cluster-backup-chart.git
cd cluster-backup-chart
helm package stable/cluster-backup-chart
</pre>

## Testing on an existing OKD cluster with OCM

Make sure you are logged in using `oc`.

<pre>
export GITHUB_TOKEN=&lt;your github personal access token&gt;
export GITHUB_USER=&lt;your github id&gt;
cd ..
git clone https://github.com/open-cluster-management/multiclusterhub-repo.git
cd cluster-backup-chart
cp cluster-backup-chart-&lt;version&gt;.tgz ../multiclusterhub-repo/multiclusterhub/charts
cd ../multiclusterhub-repo
oc annotate mch multiclusterhub -n open-cluster-management mch-pause=true
make update-charts
oc annotate mch multiclusterhub -n open-cluster-management mch-pause=false --overwrite
</pre>