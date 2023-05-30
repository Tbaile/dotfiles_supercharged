FROM continuumio/miniconda3:23.3.1-0-alpine
RUN apk add --no-cache \
        bash \
        git \
    && adduser -D -s /bin/bash dev \
    && mkdir /runtime
COPY environment.yml /runtime/environment.yml
USER dev
RUN conda init bash \
    && echo "conda activate dotfiles" >> /home/dev/.bashrc \
    && conda env create -f /runtime/environment.yml -n dotfiles \
    && conda clean -a -y
