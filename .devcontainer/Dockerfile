# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.245.2/containers/python-3/.devcontainer/base.Dockerfile

# [Choice] Python version (use -bullseye variants on local arm64/Apple Silicon): 3, 3.10, 3.9, 3.8, 3.7, 3.6, 3-bullseye, 3.10-bullseye, 3.9-bullseye, 3.8-bullseye, 3.7-bullseye, 3.6-bullseye, 3-buster, 3.10-buster, 3.9-buster, 3.8-buster, 3.7-buster, 3.6-buster
ARG VARIANT="3.10-bullseye"
FROM mcr.microsoft.com/vscode/devcontainers/python:0-${VARIANT}

# [Optional] If your pip requirements rarely change, uncomment this section to add them to the image.
# COPY requirements.txt /tmp/pip-tmp/
RUN pip3 --disable-pip-version-check --no-cache-dir install ansible-core==2.15.2 

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
     && apt-get -y install --no-install-recommends sshpass

# Set GITHUB_WORKSPACE since this devcontainer isn't run in GitHub
ENV ANSIBLE_HOME=/workspaces/ansible

# Install Ansible requirements.yml
#COPY . /ansible
#RUN ansible-galaxy collection install -p /ansible/collections -r /ansible/collections/requirements.yml --ignore-errors --force
# RUN ansible-galaxy install --roles-path /ansible/roles -r /ansible/roles/requirements.yml --ignore-errors --force
#RUN eval "$(ssh-agent -s)" && \
#     #ansible-vault view /ansible/group_vars/all/id_ed25519_lan_key | ssh-add -
#     ansible-vault view /ansible/group_vars/all/id_ed25519_lan_key --vault-password-file /home/vscode/.ansible_vault_pass.txt
WORKDIR /ansible