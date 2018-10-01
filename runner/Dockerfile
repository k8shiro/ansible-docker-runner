FROM python:2.7-alpine3.8

RUN apk update
RUN apk add gcc make git libffi-dev musl-dev openssl-dev perl py-pip python python-dev sshpass

RUN mkdir /playbook

WORKDIR /playbook

ARG ANSIBLE_VERSION="2.5.5"

RUN pip install --upgrade pip
RUN pip install ansible==$ANSIBLE_VERSION

ENV PYTHONPATH /usr/local/lib/python2.7/site-packages/

