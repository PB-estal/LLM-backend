FROM mcr.microsoft.com/devcontainers/anaconda:1-3

# Copy environment.yml (if found) to a temp location to update the environment
COPY environment.yml* .devcontainer/noop.txt /tmp/conda-tmp/
RUN if [ -f "/tmp/conda-tmp/environment.yml" ]; then \
    umask 0002 && /opt/conda/bin/conda env update -n base -f /tmp/conda-tmp/environment.yml; \
    fi && rm -rf /tmp/conda-tmp

# Copy the entire project into the container
COPY . /workspace

WORKDIR /workspace/Dev

# Install Python dependencies
RUN pip install -r /workspace/Dev/requirements.txt

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#    && apt-get -y install --no-install-recommends <your-package-list-here>
