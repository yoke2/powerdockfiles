FROM jupyter/minimal-notebook

COPY requirements.txt /tmp/
RUN pip install --requirement /tmp/requirements.txt \
    && jupyter dashboards quick-setup --sys-prefix \
    && jupyter nbextension enable --py --sys-prefix widgetsnbextension \
    && jupyter nbextension enable --py --sys-prefix ipyleaflet \
    && jupyter nbextension enable --py --sys-prefix pythreejs \
    && jupyter nbextension enable --py --sys-prefix bqplot
COPY . /tmp/
