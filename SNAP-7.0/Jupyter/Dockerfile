
FROM deltodon/esa-snap-cpython:7.0-Py3.6

LABEL maintainer="Deltodon <web@deltodon.com>"

RUN pip install jupyter -U && pip install jupyterlab

WORKDIR /workdir

EXPOSE 8888

ENTRYPOINT ["jupyter", "lab","--ip=0.0.0.0","--allow-root"]