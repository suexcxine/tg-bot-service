FROM python:3.11-slim

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    zlib1g-dev \
    libjpeg-dev \
    build-essential && \
    rm -rf /var/lib/apt/lists/*

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN mkdir /sender && apt-get update
WORKDIR /sender

COPY ./pyproject.toml /sender/
COPY ./poetry.lock /sender/
RUN pip install poetry && poetry config virtualenvs.create false && poetry install

COPY ./ /sender
