FROM docker.internal.c\b\a/library/python:3.9
LABEL maintainer='Image to Dockerfile Docker Maintainers Srirahul Nallari'

#COPY requirements.txt /usr/local/src/
#RUN pip install --no-cache-dir -r /usr/local/src/requirements.txt
#RUN mkdir -p /root/.pip
#COPY ./pip.conf /root/.pip
#RUN sed -i "s/pypi\.org/artifactory\.internal\c\b\a\/api\/pypi\/org\.python\.pypi/g" ./usr/local/lib/python3.9/site-packages/setuptools/package_index.py
RUN sed -i "s/pypi\.org/artifactory\.internal\c\b\a\/api\/pypi\/org\.python\.pypi/g" ./usr/local/lib/python3.9/site-packages/setuptools/command/easy_install.py
#RUN pip install six
COPY ./six-1.16.0.tar /
RUN tar -xvf /six-1.16.0.tar
RUN cd six-1.16.0; python3 setup.py install
COPY ./docker-5.0.3.tar.gz /
RUN tar -zxvf /docker-5.0.3.tar.gz
RUN  cd /docker-5.0.3; python3 setup.py install
RUN pip show six
COPY generate_dockerfile.py /

ENTRYPOINT [ "python", "/generate_dockerfile.py" ]
CMD [ "--help" ]

FROM hub.docker.internal.c\b\a\/alpine:3.14
