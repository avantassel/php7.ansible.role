# Dockerfile for building image that contains software stack provisioned by Ansible.
#
# USAGE:
#   $ docker build -t php7 ../
#   $ docker run -d -v $(pwd):/data php7
#
# Version  1.1
#


# pull base image
FROM williamyeh/ansible:ubuntu14.04-onbuild

MAINTAINER Chu-Siang Lai <chusiang.lai@gmail.com>


#
# build phase
#

# fix policy-rc.d for Docker
# @see http://www.monblocnotes.com/node/2057
# @see http://askubuntu.com/a/365912
RUN sed -i -e 's/exit\s\s*101/exit 0/' /usr/sbin/policy-rc.d

ENV PLAYBOOK setup.yml
RUN ansible-playbook-wrapper -vvv


#
# test phase
#

#RUN echo "===> Installing curl for testing purpose..."  && \
#    DEBIAN_FRONTEND=noninteractive  \
#    apt-get install -y -f curl

VOLUME [ "/data" ]

CMD service php7.0-fpm start && \
    tail -f /dev/null

