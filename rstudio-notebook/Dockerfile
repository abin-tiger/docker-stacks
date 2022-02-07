FROM ghcr.io/abin-tiger/docker-stacks:scipy-notebook

# install nbrsessionproxy extension
RUN conda install -c conda-forge -y jupyter-rsession-proxy && \
    conda clean -tipsy

# install rstudio-server
USER root
RUN apt-get update \
    && apt-get install -y --no-install-recommends wget \
    && rstudio_version=$(wget --no-check-certificate -qO- https://s3.amazonaws.com/rstudio-server/current.ver) \
    && wget https://download2.rstudio.org/rstudio-server-${rstudio_version}-amd64.deb -O /rstudio-server.deb \
    && apt-get install -y --no-install-recommends /rstudio-server.deb \
    && rm /rstudio-server.deb

ENV PATH=$PATH:/usr/lib/rstudio-server/bin
USER $NB_USER