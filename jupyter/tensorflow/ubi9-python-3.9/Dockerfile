ARG BASE_IMAGE
FROM ${BASE_IMAGE}

LABEL name="odh-notebook-cuda-jupyter-tensorflow-ubi9-python-3.9" \
    summary="Jupyter CUDA tensorflow notebook image for ODH notebooks" \
    description="Jupyter CUDA tensorflow notebook image with base Python 3.9 builder image based on UBI9 for ODH notebooks" \
    io.k8s.display-name="Jupyter CUDA tensorflow notebook image for ODH notebooks" \
    io.k8s.description="Jupyter CUDA tensorflow notebook image with base Python 3.9 builder image based on UBI9 for ODH notebooks" \
    authoritative-source-url="https://github.com/opendatahub-io/notebooks" \
    io.openshift.build.commit.ref="main" \
    io.openshift.build.source-location="https://github.com/opendatahub-io/notebooks/tree/main/jupyter/tensorflow/ubi8-python-3.9" \
    io.openshift.build.image="quay.io/opendatahub/notebooks:cuda-jupyter-tensorflow-ubi9-python-3.9"

# Install Python packages and Jupyterlab extensions from requirements.txt
COPY requirements.txt ./

RUN python -m pip install -r requirements.txt && \
    rm -f requirements.txt

# Fix permissions to support pip in Openshift environments
RUN chmod -R g+w /opt/app-root/lib/python3.9/site-packages && \
    fix-permissions /opt/app-root -P
