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

# workaround for psycopg2
# and netcat installing
RUN apt-get update \
    && apt-get -y install libpq-dev gcc \
    && apt-get install -y netcat \
    && pip install psycopg2

# copy project
COPY . /usr/src/app/

# install dependencies
RUN poetry install

ENTRYPOINT ["/usr/src/app/entrypoint.sh"]
