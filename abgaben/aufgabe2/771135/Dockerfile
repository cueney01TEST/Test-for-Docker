FROM ubuntu:noble AS base

FROM base AS prod-deps

RUN apt-get update && \
    apt-get -y install unminimize && \
    yes | unminimize

RUN apt-get -y install \
    binutils-doc \
    curl \
    make \
    xz-utils \
    build-essential \
    make-doc

RUN apt-get -y install openssl

WORKDIR /app
COPY ./bin/install/linux_arm_toolchain.sh ./bin/install/

RUN sed -i 's/\r$//' /app/bin/install/linux_arm_toolchain.sh && \
    chmod +x /app/bin/install/linux_arm_toolchain.sh

RUN /app/bin/install/linux_arm_toolchain.sh

ENV PATH="/opt/arm-gnu-toolchain/bin:${PATH}"

RUN useradd -m developer
USER developer

FROM prod-deps AS build

WORKDIR /app
COPY . .

CMD ["tail", "-f", "/dev/null"]
