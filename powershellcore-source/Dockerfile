FROM ubuntu:xenial
MAINTAINER Paul Amazona <whatevergeek@gmail.com>

### Install .NET Core
RUN apt-get update \
    && apt-get install apt-transport-https curl -y \
    && sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
    && apt-get update \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
    && apt-get update \
    && apt-get install dotnet-dev-1.0.0-preview2.1-003177 -y \
    && mkdir /powershell \
    && mkdir /powershell-source \
    && apt-get clean

# Install PowerShell

### Set the working directory to /powershell
WORKDIR /powershell

### Set some environment variables
ENV POWERSHELL_DOWNLOAD_URL https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-alpha.17/powershell_6.0.0-alpha.17-1ubuntu1.16.04.1_amd64.deb

RUN curl -SL $POWERSHELL_DOWNLOAD_URL --output powershell.deb \
    && apt-get install libunwind8 libicu55 \
    && dpkg --install powershell.deb \
    && rm powershell.deb \
    && apt-get clean

# Setup Powershell Build
### Set the working directory to /powershell-source
WORKDIR /powershell-source

RUN apt-get install git -y \
    && git clone --recursive https://github.com/PowerShell/PowerShell.git \
    && apt-get clean

WORKDIR /powershell-source/PowerShell
<<<<<<< HEAD

ADD script.sh /powershell-source/PowerShell/build_powershell.ps1
RUN ["powershell", "./build_powershell.ps1"]
=======
RUN powershell \
    && Import-Module ./build.psm1 \
    && Start-PSBootstrap \
    && Start-PSBuild
>>>>>>> d5099359a96661782988a8e163d53865ae5da2f2

### Install additional utilities
RUN apt-get update && apt-get install -y \
    ssh \
    tmux

ENTRYPOINT ["tmux", "-c", "powershell"]

