FROM mcr.microsoft.com/devcontainers/dotnet:1-8.0-bookworm

# Install kubectl
RUN curl -sSL -o /usr/local/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl \
    && chmod +x /usr/local/bin/kubectl

# Install Helm
RUN curl -s https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash -

COPY copy-kube-config.sh /usr/local/share/
RUN echo "source /usr/local/share/copy-kube-config.sh" | tee -a /home/vscode/.bashrc >> /home/vscode/.zshrc
