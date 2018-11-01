# Creates a docker image with python, django, and your app
# 
# Steps:
#   - Set meta information
#   - Install packages and scripts
#   - Copy requirements.txt from app
#   - Build python
#   - Copy all source code
#   - Build django app

# start from a minimal, bare-bones image
FROM alpine:latest

# set a secret key for building
ENV SECRET_KEY $satisfy-build$

# set the working directory to /app
WORKDIR /app

# install base packages
RUN apk add --no-cache bash

# copy the build scripts into image
COPY .docker/build-scripts /usr/local/sbin/

# copy hooks
COPY .docker/hooks /opt/nanobox/hooks

# copy requirements.txt into image
COPY requirements.txt .

# build python (see build-scripts)
RUN build-python-env

# copy the source code
COPY . .

# build app (see build-scripts)
RUN build-django-app
