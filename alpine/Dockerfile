FROM nginx:alpine



ARG EXPLORER_MAINNET_URL
ARG EXPLORER_TESTNET_URL

ENV APP_EXPLORER_MAINNET_URL=$EXPLORER_MAINNET_URL
ENV APP_EXPLORER_TESTNET_URL=$EXPLORER_TESTNET_URL

RUN apk update && \
    apk upgrade && \
    apk --no-cache add autoconf nginx nodejs git gifsicle libjpeg-turbo-utils optipng

# Create app directory
WORKDIR /var/www

RUN \
    git clone https://github.com/MinterTeam/minter-status-web.git && \
    cd minter-status-web && \
    npm install && npm run production

ADD https://github.com/MinterTeam/minter-status-web/config/vhost.conf /etc/nginx/conf.d/default.conf

EXPOSE 80