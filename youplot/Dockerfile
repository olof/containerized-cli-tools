# Containerized packaging for https://github.com/red-data-tools/YouPlot/issues
FROM debian:sid
RUN apt-get update \
    && apt-get --no-install-recommends -y install ruby ruby-dev build-essential \
    && gem install youplot \
    && apt-get purge -y ruby-dev build-essential \
    && apt-get autoremove -y \
    && apt-get autoclean \
    && rm -rf /var/lib/apt/lists

# The -C flag is for forcing colorized output, even without an allocated TTY.
ENTRYPOINT ["/usr/local/bin/uplot", "-C"]
