# K8s Worker Tools

This repository contains images that contain the tooling necessary to to use the execution container feature with Octopus Deploy when running commands against K8s.

- Kubectl
- Helm
- AWS IAM Authenticator
- Google's GKE Cloud Auth Plugin

There are three images built in this repo:

- Ubuntu 20.04
- Ubuntu 18.04
- Windows 2019

A new image will be built each time a new version of `kubectl` is created.  The version numbers will be based on the version of `kubectl`.

**Please consider this repository provided as is.  If there are any issues please do not contact support.**