# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.245.0/containers/python-3/.devcontainer/base.Dockerfile

# [Choice] Python version (use -bullseye variants on local arm64/Apple Silicon): 3, 3.10, 3.9, 3.8, 3.7, 3.6, 3-bullseye, 3.10-bullseye, 3.9-bullseye, 3.8-bullseye, 3.7-bullseye, 3.6-bullseye, 3-buster, 3.10-buster, 3.9-buster, 3.8-buster, 3.7-buster, 3.6-buster
ARG VARIANT="3.7-bullseye"
FROM mcr.microsoft.com/vscode/devcontainers/python:0-${VARIANT}

RUN apt-get update && apt-get install -y ffmpeg libsm6 libxext6

# [Optional] If your pip requirements rarely change, uncomment this section to add them to the image.
COPY src/requirements.deploy.txt /tmp/pip-tmp/
COPY src/requirements.txt /tmp/pip-tmp/
RUN pip install -U pytest
RUN pip --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
    && pip --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.deploy.txt \
    && rm -rf /tmp/pip-tmp
