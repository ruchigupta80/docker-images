# Copyright (c) 2016-2020 Crave.io Inc. All rights reserved
FROM accupara/qt5:linux32
MAINTAINER Crave.io Inc. "contact@crave.io"

# Keep the update separate so that Docker build system can cache it.
RUN sudo apt-get update
RUN sudo apt-get install -y \
        libc6-amd64 \
        libtelepathy-qt5-dev \
        perl \
        qt5-default
