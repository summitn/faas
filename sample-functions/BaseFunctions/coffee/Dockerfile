FROM node:6.9.1-alpine

ADD https://github.com/openfaas/faas/releases/download/0.9.0/fwatchdog /usr/bin
RUN chmod +x /usr/bin/fwatchdog

WORKDIR /root/

COPY package.json .

RUN npm install -g coffee-script && \
    npm i

COPY handler.coffee .

ENV fprocess="coffee handler.coffee"

HEALTHCHECK --interval=1s CMD [ -e /tmp/.lock ] || exit 1

CMD ["fwatchdog"]
