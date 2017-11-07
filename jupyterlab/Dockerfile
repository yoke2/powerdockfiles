FROM continuumio/miniconda3

COPY requirements.txt /tmp/
RUN pip install --requirement /tmp/requirements.txt \
    && jupyter serverextension enable --py jupyterlab --sys-prefix \
    && jupyter labextension install @jupyterlab/google-drive 
COPY . /tmp/
