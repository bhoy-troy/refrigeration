
## Dockerfile Lint

    docker run --rm -i hadolint/hadolint < images/Dockerfile

## Run with Compose

    docker-compose up

## Build the docker container

    docker build --tags tensorflow-notebook -f images/Dockerfile


## Run in a Docker container
    
    docker run --rm -p 8888:8888 \
        -e JUPYTER_ENABLE_LAB=yes  \
        -e CHOWN_HOME=yes \
        -e RESTARTABLE=yes \
        -v "${PWD}/jovyan/work":/home/jovyan/work \
        -f ./images/Dockerfile


## Add a formatter

Note the formatter is applied to the container in the docker image

    jupyter contrib nbextension install --user
    jupyter nbextension install https://github.com/drillan/jupyter-black/archive/master.zip --user
    jupyter nbextension
    jupyter nbextension enable codefolding/main


### House keeping


    nbqa black refrigeration.ipynb --nbqa-mutate
    nbqa isort refrigeration.ipynb --nbqa-mutate 
    nbqa doctestmart_meter_energy.ipynb


# To Latex

    jupyter nbconvert --to markdown refrigeration.ipynb
    
    pandoc --listings -f markdown -t latex refrigeration.md -o refrigeration.tex

    jupyter nbconvert --to webpdf refrigeration.ipynb --allow-chromium-download
    
    jupyter nbconvert --to notebook refrigeration.ipynb
    
    jupyter nbconvert myslides.ipynb --to slides --post serve