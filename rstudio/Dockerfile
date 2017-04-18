FROM rocker/rstudio

MAINTAINER "Paul Amazona" whatevergeek@gmail.com

# from the tensorflow dockerfile: 
# https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/docker/Dockerfile

# Pick up some TF dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        curl \
        libfreetype6-dev \
        libzmq3-dev \
        pkg-config \
        python \
        python-dev \
        rsync \
        software-properties-common \
        unzip \
        && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py && \
    rm get-pip.py

RUN pip --no-cache-dir install \
        ipykernel \
        jupyter \
        matplotlib \
        numpy \
       scipy \
        && \
    python -m ipykernel.kernelspec

RUN pip --no-cache-dir install \
  --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.11.0rc0-cp27-none-linux_x86_64.whl

RUN install2.r --error \
    devtools

RUN R -e "devtools::install_github('rstudio/tensorflow')"

RUN R -e "install.packages('tidyverse')" && \
    R -e "install.packages('plotly')" && \
    R -e "install.packages('AzureML')" && \
    R -e "install.packages('swirl')" && \
    R -e "install.packages('rattle')" && \
    R -e "install.packages('sqldf')" && \
    R -e "install.packages('forecast')" && \
    R -e "install.packages('tm')" && \
    R -e "install.packages('xkcd')" && \
    R -e "install.packages('shiny')" && \ 
    R -e "install.packages('flexdashboard')" && \
    R -e "install.packages('evaluate')" && \ 
    R -e "install.packages('formatR')" && \ 
    R -e "install.packages('highr')" && \ 
    R -e "install.packages('markdown')" && \ 
    R -e "install.packages('yaml')" && \ 
    R -e "install.packages('caTools')" && \
    R -e "install.packages('bitops')" && \
    R -e "install.packages('knitr')" && \ 
    R -e "install.packages('base64enc')" && \ 
    R -e "install.packages('rprojroot')" && \ 
    R -e "install.packages('shiny')" && \ 
    R -e "install.packages('biclust')" && \
    R -e "install.packages('rmarkdown')" && \
    R -e "install.packages('googleVis')" && \
    R -e "install.packages('bookdown')" && \
    R -e "install.packages('RODBC')" && \
    R -e "install.packages('RSQLite')" && \
    R -e "install.packages('randomForest')" && \
    R -e "install.packages('fivethirtyeight')" && \
    R -e "install.packages('leaflet')" 

RUN R -e "devtools::install_github('ramnathv/rCharts@dev')"
RUN R -e "devtools::install_github('ramnathv/rMaps')"
RUN R -e "devtools::install_github('rstudio/shinygadgets')"
RUN R -e "install.packages('gapminder')"
RUN R -e "devtools::install_github('joyofdata/RTwitterAPI')"

CMD ["/init"]
