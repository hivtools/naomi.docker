FROM rocker/r-ver:4

ENV PANDOC_VER=2.11.0.2

RUN apt-get update && apt-get -y install --no-install-recommends \
        libcurl4-openssl-dev \
        libgdal-dev \
        libhiredis-dev \
        libjq-dev \
        libprotobuf-dev \
        libssh-dev \
        libsodium-dev \
        libudunits2-dev \
        libv8-dev \
        libxml2-dev \
        protobuf-compiler \
        texinfo \
        texlive \
        texlive-fonts-extra \
        texlive-latex-extra \
        wget \
        zlib1g-dev \
        && apt-get clean \
        && rm -rf /var/lib/apt/lists/*
        
## Install pandoc
RUN cd /opt && wget https://github.com/jgm/pandoc/releases/download/$PANDOC_VER/pandoc-$PANDOC_VER-1-amd64.deb \
    && dpkg -i pandoc-$PANDOC_VER-1-amd64.deb \
    && apt-get -y autoremove && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /opt/*

COPY docker/bin /usr/local/bin/
COPY docker/Rprofile.site /usr/local/lib/R/etc/Rprofile.site

RUN install_packages --repo=https://mrc-ide.r-universe.dev \
        DBI \
        DiagrammeR \
        Matrix \
        R6 \
        RcppEigen \
        TMB \
        assertthat \
        covr \
        data.tree \
        docopt \
        dplyr \
        duckdb \
        eppasm \
        first90 \
        forcats \
        geojsonio \
        ggplot2 \
        glue \
        gridExtra \
        gt \
        heartbeatr \
        here \
        jsonlite \
        jsonvalidate \
        knitr \
        lubridate \
        magrittr \
        methods \
        mockery \
        mvtnorm \
        naomi.options \
        plotly \
        plumber \
        porcelain \
        ps \
        qs \
        readr \
        remotes \
        rlang \
        rmarkdown \
        rrq \
        scales \
        sf \
        spdep \
        specio \
        survey \
        testthat \
        tidyr \
        tidyverse \
        traduire \
        viridis \
        withr \
        writexl \
        yaml \
        zip \
        zoo

RUN install_packages remotes && install_remote \
        bergant/datamodelr
