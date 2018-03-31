# minimal-notebook image as of 20180220
FROM jupyter/minimal-notebook:92fe05d1e7e5

COPY requirements.txt /tmp/
RUN pip install --requirement /tmp/requirements.txt
RUN wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
RUN export NVM_DIR="$HOME/.nvm"
RUN [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
RUN nvm install 8.11.1
RUN jupyter labextension install @jupyterlab/plotly-extension
COPY . /tmp/
