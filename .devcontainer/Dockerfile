FROM python:3.14
ARG UID=1000
ARG GID=1000
RUN addgroup --gid ${GID} dev \
    && adduser --gid ${GID} --uid ${UID} --disabled-password --shell /bin/bash dev \
    && pip install --root-user-action ignore poetry
USER dev
