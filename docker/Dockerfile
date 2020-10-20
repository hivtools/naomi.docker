FROM rocker/r-ver:4.0.2

ENV PANDOC_VER=2.2.2.1

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

RUN install_packages --repo=https://mrc-ide.github.io/drat \
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
        plumber \
        ps \
        rdhs \
        readr \
        remotes \
        rlang \
        rmarkdown \
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
        yaml \
        zip \
        zoo

RUN install_packages remotes && install_remote \
        bergant/datamodelr \
        mrc-ide/eppasm \
        reside-ic/pkgapi \
        mrc-ide/rrq

