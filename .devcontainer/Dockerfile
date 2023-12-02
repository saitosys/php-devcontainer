ARG STACK_ID=22

FROM mcr.microsoft.com/vscode/devcontainers/base:0-ubuntu-${STACK_ID}.04
ARG STACK_ID
ARG STACK=heroku-${STACK_ID}

ADD https://raw.githubusercontent.com/heroku/stack-images/main/${STACK}/setup.sh /tmp/setup.sh
RUN chmod +x /tmp/setup.sh && /tmp/setup.sh

ADD https://raw.githubusercontent.com/heroku/stack-images/main/${STACK}-build/setup.sh /tmp/setup.sh
RUN chmod +x /tmp/setup.sh && /tmp/setup.sh

# Brew requirements https://docs.brew.sh/Homebrew-on-Linux#requirements
RUN apt-get update -qq; \
    apt-get install -y --no-install-recommends install \
    build-essential procps curl file git; \
    apt-get clean -y && rm -rf /var/lib/apt/lists/* /tmp/library-scripts

ENV STACK=${STACK}
