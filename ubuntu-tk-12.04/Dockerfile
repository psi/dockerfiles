FROM ubuntu:12.04
MAINTAINER JD Harrington <jd@jdharrington.net>

RUN apt-get update --yes
RUN apt-get install curl --yes
RUN curl -L https://www.chef.io/chef/install.sh | bash

ENV BUSSER_ROOT=/opt/busser
ENV GEM_HOME=/opt/busser/gems
ENV GEM_PATH=/opt/busser/gems
ENV GEM_CACHE=/opt/busser/gems/cache

RUN /opt/chef/embedded/bin/gem install busser --no-rdoc --no-ri
RUN /opt/chef/embedded/bin/gem install serverspec --no-rdoc --no-ri
RUN /opt/busser/gems/bin/busser setup
RUN /opt/busser/gems/bin/busser plugin install busser-serverspec
