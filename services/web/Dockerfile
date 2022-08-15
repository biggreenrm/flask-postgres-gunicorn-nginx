# pull official base image
FROM python:3.10-slim-buster

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV POETRY_VERSION 1.1.13

# install poetry
RUN set -ex; pip install --no-cache-dir poetry==$POETRY_VERSION; \
    poetry config virtualenvs.create false

# copy project
COPY . /usr/src/app/

# install dependencies
RUN poetry install
