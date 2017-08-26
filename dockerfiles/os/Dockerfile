FROM ubuntu:16.04
ENV DEBIAN_FRONTEND noninteractive
ENV PYTHONBUFFERED 1
COPY ./dockerfiles/judger/sources.list /etc/apt/sources.list
RUN apt-get update \
    && buildDeps=' \
		software-properties-common \
		python-software-properties \
		python-dev \
		git \
		libtool \
		python-pip \
		libtool \
		libseccomp-dev' \
    && apt-get -y install --no-install-recommends python gcc g++ python-pkg-resources $buildDeps\
    && add-apt-repository -y ppa:webupd8team/java \
    && echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
    && echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections \
    && apt-get update \
    && apt-get install -y --no-install-recommends oracle-java8-installer \
    && apt-get install --no-install-recommends -y nginx python-pip \ 
    && nodejs libmysqlclient-dev python-setuptools build-essential python-dev
CMD bash
