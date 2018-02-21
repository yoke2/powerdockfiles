# minimal-notebook image as of 20180220
FROM jupyter/minimal-notebook:92fe05d1e7e5

COPY requirements.txt /tmp/
RUN pip install --requirement /tmp/requirements.txt
COPY . /tmp/
