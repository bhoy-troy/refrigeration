FROM jupyter/tensorflow-notebook:python-3.8.8

USER root
RUN apt-get update -y && \
    DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y \
        gcc \
        g++ && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists/*
USER ${NB_USER}

COPY requirements.txt /tmp/
RUN pip install --quiet --no-cache-dir -r /tmp/requirements.txt && \
    jupyter nbextension install https://github.com/drillan/jupyter-black/archive/master.zip --user && \
    jupyter nbextension enable jupyter-black-master/jupyter-black
