FROM myoj/os:latest
ENV PYTHONBUFFERED 1
ADD . /code
WORKDIR /code
RUN pip install -i https://pypi.douban.com/simple -r dockerfiles/oj_web_server/requirements.txt 
RUN python tools/release_static.py
CMD bash /code/dockerfiles/oj_web_server/run.sh
