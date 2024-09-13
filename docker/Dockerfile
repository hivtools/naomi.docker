FROM rhub/r-minimal

ENV PANDOC_VER=2.11.0.2

RUN wget https://github.com/jgm/pandoc/releases/download/$PANDOC_VER/pandoc-$PANDOC_VER-linux-amd64.tar.gz && \
    tar xzf pandoc-$PANDOC_VER-linux-amd64.tar.gz && \
    mv pandoc-$PANDOC_VER/bin/* /usr/local/bin/ && \
    rm -rf pandoc-$PANDOC_VER*

RUN installr -d \
    -t "libsodium-dev curl-dev linux-headers openssl-dev gfortran proj-dev gdal-dev sqlite-dev geos-dev udunits-dev protobuf-dev jq-dev libxml2-dev fontconfig-dev" \
    -a "libsodium libssl3 proj gdal geos expat udunits fontconfig jq" \
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
    duckdb \
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
	openxlsx \
    plotly \
    plumber \
    qs \
    readr \
    remotes \
    rlang \
    rmarkdown \
    sf \
    spdep \
    svglite \
    tidyr \
    withr \
    writexl \
    yaml \
    zip \
    zoo

# TODO: Install a non-hardcoded version of these
# I think should be doable by adding R-universe to the repos option via Rprofile
RUN installr -d \
    -t "linux-headers" \
    -a "hiredis-dev" \
    url::https://mrc-ide.r-universe.dev/src/contrib/rrq_0.7.17.tar.gz \
    url::https://mrc-ide.r-universe.dev/src/contrib/heartbeatr_0.6.0.tar.gz \
    url::https://mrc-ide.r-universe.dev/src/contrib/eppasm_0.7.6.tar.gz \
    url::https://mrc-ide.r-universe.dev/src/contrib/first90_1.6.11.tar.gz \
    url::https://mrc-ide.r-universe.dev/src/contrib/naomi.options_1.2.1.tar.gz \
    url::https://mrc-ide.r-universe.dev/src/contrib/porcelain_0.1.15.tar.gz \
    url::https://mrc-ide.r-universe.dev/src/contrib/specio_0.1.4.tar.gz

RUN apk add binutils \
    && find / -type f -name "*.so" -exec strip --strip-all {} + || true \
    && apk del binutils
