# Use an official Node.js image as a base
FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu-22.04

ARG ARCH

# Install dependencies
RUN apt-get update && apt-get install -y \
    curl \
    gnupg2 \
    software-properties-common \
    unzip \
    ca-certificates  # Install CA certificates

# Install AWS CLI
RUN if [ "${ARCH}" = "arm64" ]; then ARCH=aarch64; fi && \
    curl "https://awscli.amazonaws.com/awscli-exe-linux-${ARCH}.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf awscliv2.zip aws

# Install eksctl# Install eksctl
RUN if [ "${ARCH}" = "x86_64" ]; then ARCH=amd64; fi && \
    echo "https://github.com/weaveworks/eksctl/releases/download/v0.155.0/eksctl_$(uname -s)_${ARCH}.tar.gz" && \
    curl --silent --location "https://github.com/weaveworks/eksctl/releases/download/v0.155.0/eksctl_$(uname -s)_${ARCH}.tar.gz" | tar xz -C /tmp && \
    sudo mv /tmp/eksctl /usr/local/bin

# Install Terraform
RUN if [ "${ARCH}" = "x86_64" ]; then ARCH=amd64; fi && \
    curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - && \
    apt-add-repository "deb [arch=${ARCH}] https://apt.releases.hashicorp.com $(lsb_release -cs) main" && \
    apt-get update && \
    apt-get install -y terraform

# Install kubectl
RUN if [ "${ARCH}" = "x86_64" ]; then ARCH=amd64; fi && \
    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/${ARCH}/kubectl" && \
    install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl && \
    rm kubectl

# Install kubectx and kubens
RUN git clone https://github.com/ahmetb/kubectx /opt/kubectx && \
    ln -s /opt/kubectx/kubectx /usr/local/bin/kubectx && \
    ln -s /opt/kubectx/kubens /usr/local/bin/kubens

# Install Helm
RUN curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Set up alias for kubectl globally
RUN echo 'alias k=kubectl' >> /etc/bash.bashrc

# Verify installations
RUN aws --version && \
    eksctl version && \
    terraform -version && \
    kubectl version --client && \
    kubectx --help && \
    kubens --help && \
    helm version
