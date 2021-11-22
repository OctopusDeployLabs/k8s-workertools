# escape=`

FROM octopuslabs/workertools:latest-windows.2019
SHELL ["powershell", "-Command"]

RUN choco install kubernetes-cli -y --no-progress

RUN choco install -y kubernetes-helm --no-progress

RUN choco install eksctl -y --no-progress

RUN choco install aws-iam-authenticator -y --no-progress

# # Install Azure CLI
RUN choco install azure-cli -y --no-progress

RUN Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force; `
    Install-Module -Force -Name Az -AllowClobber -Scope AllUsers