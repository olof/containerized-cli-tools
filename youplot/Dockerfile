FROM debian:sid
RUN apt-get update && apt-get --no-install-recommends -y install ruby ruby-dev
RUN apt-get install --no-install-recommends -y build-essential
RUN gem install youplot
ENTRYPOINT ["/usr/local/bin/uplot", "-C"]
