# K8s Worker Tools

This repository contains images that contain the tooling necessary to to use the execution container feature with Octopus Deploy when running commands against K8s.

- Kubectl
- Helm
- AWS IAM Authenticator
- Google's GKE Cloud Auth Plugin

The following images are built in this repo:

- Ubuntu 22.04
- Ubuntu 20.04 (tagged `latest` in [DockerHub](https://hub.docker.com/r/octopuslabs/k8s-workertools/tags?page=1&name=latest))
- Windows 2019 (tagged `latest` in [DockerHub](https://hub.docker.com/r/octopuslabs/k8s-workertools/tags?page=1&name=latest))

A new image will be built each time a new version of `kubectl` is created.  The version numbers will be based on the version of `kubectl`.

**Please consider this repository provided as is.  If there are any issues please do not contact support.**