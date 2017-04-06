FROM jupyter/minimal-notebook:9e056d61b7a5

COPY requirements.txt /tmp/
RUN pip install --requirement /tmp/requirements.txt
COPY . /tmp/

# Install R
USER root
WORKDIR /tmp

COPY install_irkernel.R /tmp/install_irkernel.R 

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9 && \
    add-apt-repository 'deb [arch=amd64,i386] https://cran.rstudio.com/bin/linux/ubuntu xenial/' && \
    apt-get update && \
    apt-get upgrade -y -o Dpkg::Options::="--force-confold" && \
    apt-get install -y --no-install-recommends r-base \
            libssl-dev \
            libcairo2-dev \
            libcurl4-openssl-dev && \
    R --no-save < /tmp/install_irkernel.R && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Upgrade Jupyter Notebook
RUN pip install --upgrade notebook 

WORKDIR $DOCKER_HOME