FROM python:3.11-slim

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    zlib1g-dev \
    libjpeg-dev \
    build-essential && \
    rm -rf /var/lib/apt/lists/*

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN mkdir /receiver && apt-get update
WORKDIR /receiver

COPY ./pyproject.toml /receiver/
COPY ./poetry.lock /receiver/
RUN pip install poetry && poetry config virtualenvs.create false && poetry install

COPY ./ /receiver
