FROM fedora:37
COPY fedora-requirements.txt /tmp/fedora-requirements.txt
RUN echo "max_parallel_downloads=10" >> /etc/dnf/dnf.conf \
    && dnf install -y \
        $(cat /tmp/fedora-requirements.txt) \
        git \
        sudo \
    && rm -f /tmp/fedora-requirements.txt \
    && echo "ALL ALL=(ALL:ALL) NOPASSWD: ALL" > "/etc/sudoers.d/password_less_sudo"
# create main user
RUN useradd --user-group --shell /bin/bash --create-home code
USER code
RUN mkdir /tmp/dotfiles
COPY requirements.txt /tmp/dotfiles/
COPY roles/requirements.yml /tmp/dotfiles/
RUN pip install --user -r /tmp/dotfiles/requirements.txt \
    && /home/code/.local/bin/ansible-galaxy install -r /tmp/dotfiles/requirements.yml
