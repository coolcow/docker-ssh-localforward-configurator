FROM python:latest

COPY servicesToSshConf.py /
RUN chmod +x /servicesToSshConf.py

WORKDIR /tmp

ENTRYPOINT ["/servicesToSshConf.py"]
