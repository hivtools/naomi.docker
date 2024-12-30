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
        xz-utils \
        zlib1g-dev \
        && apt-get clean \
        && rm -rf /var/lib/apt/lists/*

## Install pandoc
RUN cd /opt && wget https://github.com/jgm/pandoc/releases/download/$PANDOC_VER/pandoc-$PANDOC_VER-1-amd64.deb \
    && dpkg -i pandoc-$PANDOC_VER-1-amd64.deb \
    && apt-get -y autoremove && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /opt/*

COPY docker/bin /usr/local/bin/
COPY docker/Rprofile.site /usr/local/lib/R/etc/Rprofile.site

RUN install_packages --repo=https://duckdb.r-universe.dev \
        duckdb

RUN install_packages --repo=https://mrc-ide.r-universe.dev \
        DBI \
        Matrix \
        R6 \
        RcppEigen \
        TMB \
        assertthat \
        brio \
        callr \
        data.tree \
        docopt \
        dplyr \
        eppasm \
        first90 \
        forcats \
        geojsonio \
        ggplot2 \
        glue \
        gt \
        jsonlite \
        knitr \
        lgr \
        magrittr \
        methods \
        mvtnorm \
        naomi.options \
        openxlsx \
        plotly \
        plumber \
        porcelain \
        qs \
        readr \
        remotes \
        rlang \
        rmarkdown \
        rrq \
        sf \
        spdep \
        specio \
        tidyr \
        traduire \
        withr \
        writexl \
        yaml \
        zip \
        zoo

RUN apt-get -y install --no-install-recommends binutils \
    && find / -type f -name "*.so" -exec strip --strip-all {} + || true
