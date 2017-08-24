FROM ubuntu:16.04
ENV PYTHONBUFFERED 1
RUN apt-get update \
    &&apt-get install --no-install-recommends -y nginx python-pip \ 
       nodejs libmysqlclient-dev python-setuptools build-essential python-dev \
    && apt-get purge -y --auto-remove build-essential python-dev\
    && rm -rf /var/lib/apt/lists/*
CMD bash
