---
title: "Saturation PreFlight"
date: 2020-05-14
weight: 4
description: >
  A simple PreFlight application with saturation optmization
---

The tutorial repository contains the Kubernetes manifests and sample configuration files
required to deploy the simple load capable testing app used by Opsani. If you have 
a Kubernetes cluster running, you can simply run the `start.sh` script to configure 
the required service account and launch servo, and the sample application.  It will
also generate a secret with your Account Token, assuming you've written it into the
file called config.yaml along with the rest of the parameters.

If you don't have a Kubernetes cluster running, we recommend using the eksctl tool for 
deployment on AWS, or the simple launch script in Google. With Google, don't forget to 
enable the admin service account (which is described in the GKE launch wizard). 
[KinD] or [Minikube] may also be viable as long as the machine either of these which they
are launched has a minimum of 8 threads (4 Hyperthreaded cores) and 16GB of RAM available.

## Ensure you can reach your Kubernetes cluster

```bash
kubectl get nodes
```

## Deploy the simple web app

Run the `configure.sh` script:

```bash
sh ./configure.sh
```

Log in to your Opsani Console [console]
Navigate to your application, and have a look at the logs section.

[`console`][console]

An alterate way to look at logs are to capture them from the Servo:

```bash
kubectl logs -f $(kubectl get pods -o jsonpath='{.items[?(@.metadata.labels.comp=="opsani-servo")].metadata.name}')
```

Tested on `Kubernetes 1.15.2`.

[kubectl]: https://kubernetes.io/docs/tasks/tools/install-kubectl/
[eksctl]: https://eksctl.io/introduction/installation/
[coctl]: https://github.com/opsani/coctl/
[console]: https://console.opsani.com/
[KinD]: https://kind.sigs.k8s.io/docs/user/quick-start/
[Minikube]: https://kubernetes.io/docs/tasks/tools/install-minikube/

