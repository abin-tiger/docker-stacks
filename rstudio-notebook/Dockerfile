FROM ghcr.io/abin-tiger/docker-stacks:scipy-notebook

# install nbrsessionproxy extension
RUN pip install --no-cache-dir jupyter-rsession-proxy

# install rstudio-server
USER root

ENV RSTUDIO_VERSION "2021.09.2-382"
# Make sure RStudio run when booting the image
ENV RSESSION_PROXY_RSTUDIO_1_4=yes

RUN apt-get update \
    && apt-get install -y --no-install-recommends curl \
    && curl --silent -L --fail https://download2.rstudio.org/server/bionic/amd64/rstudio-server-${RSTUDIO_VERSION}-amd64.deb > /tmp/rstudio.deb && \
    apt install -y /tmp/rstudio.deb && \
    rm /tmp/rstudio.deb && \
    apt clean && rm -rf /var/lib/apt/lists/* 
ENV PATH=$PATH:/usr/lib/rstudio-server/bin
USER $NB_USER