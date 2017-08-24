FROM ubuntu:16.04
ENV DEBIAN_FRONTEND noninteractive
RUN cd /tmp \
    && git clone -b master https://github.com/gaeolus/Judger \
    && cd Judger \
    && python setup.py install \
    && pip install supervisor \
    && apt-get purge -y --auto-remove $buildDeps \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /var/judger/run/ \
    && mkdir /var/judger/test_case/ \
    && mkdir /var/judger/code/ \
    && chmod -R 777 /var/judger/run/
COPY dockerfiles/judger/policy /var/judger/run
COPY dockerfiles/judger/supervisord.conf /etc
ADD . /var/judger/code
WORKDIR /var/judger/code/judge/
EXPOSE 8080
CMD bash /var/judger/code/dockerfiles/judger/run.sh

