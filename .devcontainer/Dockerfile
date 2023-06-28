FROM continuumio/miniconda3:23.3.1-0-alpine
ARG UID=1000
ARG GID=1000
RUN apk add --no-cache \
        bash \
        git \
    && addgroup -g ${GID} dev \
    && adduser -G dev -u ${UID} -D -s /dev/sh dev \
    && mkdir /runtime
COPY environment.yml /runtime/environment.yml
USER dev
RUN conda init bash \
    && echo "conda activate dotfiles" >> /home/dev/.bashrc \
    && conda env create -f /runtime/environment.yml -n dotfiles \
    && conda clean -a -y
COPY roles/requirements.yml /runtime/requirements.yml
RUN /home/dev/.conda/envs/dotfiles/bin/ansible-galaxy collection install -r /runtime/requirements.yml
