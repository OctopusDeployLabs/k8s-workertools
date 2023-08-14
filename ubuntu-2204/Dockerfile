FROM octopuslabs/workertools:latest-ubuntu.2204

ARG DEBIAN_FRONTEND noninteractive

# Get kubectl
# https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#install-using-native-package-management
RUN curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | gpg --dearmor -o /usr/share/keyrings/kubernetes-archive-keyring.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | tee /etc/apt/sources.list.d/kubernetes.list && \
    apt-get update && apt-get install -y kubectl

# Install git
RUN apt-get update && apt-get install -y git 

# Get latest Helm v3
RUN wget --quiet -O - https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Get Kubelogin
RUN wget --quiet https://github.com/Azure/kubelogin/releases/latest/download/kubelogin-linux-amd64.zip && \
    unzip kubelogin-linux-amd64.zip -d kubelogin-linux-amd64 && \
    mv kubelogin-linux-amd64/bin/linux_amd64/kubelogin /usr/local/bin && \
    rm -rf kubelogin-linux-amd64 && \
    rm kubelogin-linux-amd64.zip
    
# Get EKS CLI
# https://github.com/weaveworks/eksctl
RUN curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp && \
    mv /tmp/eksctl /usr/local/bin

# Get aws-cli
# https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
RUN curl --silent -L "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -f awscliv2.zip

# Get gke-gcloud-auth-plugin (reqd for kubectl 1.26+)
# See https://github.com/OctopusDeploy/Issues/issues/7621 for more info
RUN curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && \
    apt-get update && apt-get install -y google-cloud-sdk-gke-gcloud-auth-plugin

# Get the Istio CLI
# https://istio.io/docs/ops/diagnostic-tools/istioctl/
RUN curl -sL https://istio.io/downloadIstioctl | sh - && \
    mv /root/.istioctl/bin/istioctl /usr/local/bin/istioctl && \
    rm -rf /root/.istioctl

# Get the Linkerd CLI
# https://linkerd.io/2/getting-started/
RUN curl -sL https://run.linkerd.io/install | sh && \
    cp /root/.linkerd2/bin/linkerd /usr/local/bin && \
    rm -rf /root/.linkerd2

# Skopeo
# https://github.com/containers/skopeo/blob/master/install.md
RUN sh -c "echo 'deb http://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_18.04/ /' > /etc/apt/sources.list.d/devel:kubic:libcontainers:stable.list" && \
    wget -nv https://download.opensuse.org/repositories/devel:kubic:libcontainers:stable/xUbuntu_18.04/Release.key -O- | apt-key add - && \
    apt-get update && apt-get install -y skopeo

# Get Azure CLI
# https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

# JQ
RUN apt-get install -y jq

# Get AZ Powershell core modules
# https://docs.microsoft.com/en-us/powershell/azure/install-az-ps?view=azps-3.6.1
RUN pwsh -c 'Install-Module -Force -Name Az -AllowClobber -Scope AllUsers'