# escape=`

FROM octopuslabs/workertools:latest-windows.2019
SHELL ["powershell", "-Command"]

RUN choco install kubernetes-cli -y --no-progress

RUN choco install -y kubernetes-helm --no-progress

RUN choco install eksctl -y --no-progress

run choco install aws-iam-authenticator -y --no-progress