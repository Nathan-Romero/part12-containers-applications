FROM node:trixie-slim

RUN apt-get update \
  && apt-get install -y --no-install-recommends dumb-init \
  && apt-get clean

ENV NODE_ENV=production

WORKDIR /usr/src/app

COPY --chown=node:node . /usr/src/app

RUN npm ci --omit=dev

ENV DEBUG=todo-express-backend:*

USER node

ENTRYPOINT ["/usr/bin/dumb-init", "--"]

CMD ["node", "./bin/www"]