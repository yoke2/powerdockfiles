FROM jupyter/minimal-notebook

COPY requirements.txt /tmp/
RUN pip install --requirement /tmp/requirements.txt
RUN jupyter dashboards quick-setup --sys-prefix
COPY . /tmp/
