
Dockerfile Lint

    docker run --rm -i hadolint/hadolint < images/Dockerfile


    docker-compose up

    docker build --tags tensorflow-notebook -f images/Dockerfile
    docker run --rm -p 8888:8888 \
        -e JUPYTER_ENABLE_LAB=yes  \
        -e CHOWN_HOME=yes \
        -e RESTARTABLE=yes \
        -v "${PWD}/jovyan/work":/home/jovyan/work \
        -f ./images/Dockerfile


Add a formatter

    docker exec -it tensorflow-notebook sh
    jupyter labextension install jupyterlab-cell-formatter-black


    docker exec -it thesis_datascience-notebook_1 sh

    conda install  --yes black && \
    conda clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

  
    jupyter nbextension install https://github.com/drillan/jupyter-black/archive/master.zip
    jupyter nbextension
    jupyter nbextension install --sys-prefix --symlink --py jupyter_dash
    jupyter nbextension enable --py jupyter_dash

    jupyter labextension install jupyterlab-cell-formatter-black