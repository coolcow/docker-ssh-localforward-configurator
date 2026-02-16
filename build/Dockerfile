ARG PYTHON_VERSION=3.14.3
FROM python:${PYTHON_VERSION}

COPY servicesToSshConf.py /usr/local/bin/servicesToSshConf.py
RUN chmod +x /usr/local/bin/servicesToSshConf.py

WORKDIR /tmp

ENTRYPOINT ["/usr/local/bin/servicesToSshConf.py"]
