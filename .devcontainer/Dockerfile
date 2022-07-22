# [Choice] Python version: 3, 3.8, 3.7, 3.6
ARG VARIANT=3
FROM python:3.10

ENV PYTHONUNBUFFERED 1

# Update args in docker-compose.yaml to set the UID/GID of the "vscode" user.
# ARG USER_UID=1000
# ARG USER_GID=$USER_UID
# RUN if [ "$USER_GID" != "1000" ] || [ "$USER_UID" != "1000" ]; then groupmod --gid $USER_GID vscode && usermod --uid $USER_UID --gid $USER_GID vscode; fi

# [Option] Install Node.js
# ARG INSTALL_NODE="true"
# ARG NODE_VERSION="lts/*"
# RUN if [ "${INSTALL_NODE}" = "true" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# [Optional] If your requirements rarely change, uncomment this section to add them to the image.
# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

COPY . /root/workspace
RUN pip3 install --upgrade pip

#install poetry
RUN pip3 install poetry
#use system python instead of venv
RUN poetry config virtualenvs.create false
RUN cd /root/workspace && poetry install --no-dev