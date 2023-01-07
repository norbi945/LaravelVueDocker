FROM 'ubuntu'

RUN apt-get update && apt-get install -y build-essential

RUN apt -yq install nginx
RUN bash -c "service nginx start"

ENV NODE_VERSION 14.16.1

RUN apt -yq install wget
RUN wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
RUN . ~/.nvm/nvm.sh \
    && nvm install ${NODE_VERSION} \
    && nvm alias default ${NODE_VERSION} \
    && nvm use default

ENV PATH /versions/node/v${NODE_VERSION}/bin:$PATH

# The following is needed for the lts version of node (at the time I wrote this, it was 18.x.x)
# RUN export NODE_OPTIONS=--openssl-legacy-provider