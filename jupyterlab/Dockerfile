# minimal-notebook image as of 20180220
FROM jupyter/minimal-notebook:92fe05d1e7e5

# make sure apt is up to date
RUN /bin/bash apt-get update --fix-missing
RUN /bin/bash apt-get install -y curl
RUN /bin/bash sudo apt-get install -y build-essential libssl-dev

ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION 8.11.1

# Install nvm with node and npm
RUN curl https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | /bin/bash \
    && /bin/bash -c "source $NVM_DIR/nvm.sh" \
    && nvm install $NODE_VERSION \
    && nvm alias default $NODE_VERSION \
    && nvm use default

ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH      $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

# Install python dependencies
COPY requirements.txt /tmp/
RUN pip install --requirement /tmp/requirements.txt
RUN jupyter labextension install @jupyterlab/plotly-extension
COPY . /tmp/
