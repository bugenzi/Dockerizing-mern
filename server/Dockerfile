FROM node:14 AS BUILD_IMAGE

RUN curl -sfL https://install.goreleaser.com/github.com/tj/node-prune.sh | bash -s -- -b /usr/local/bin

WORKDIR /app/server

COPY ./ /app/server/

RUN npm install && npm prune --production

RUN /usr/local/bin/node-prune


FROM node:14.18.0-alpine

WORKDIR /app/server

# copy from build image
COPY --from=BUILD_IMAGE /app/server/ /app/server/

RUN npm install 


CMD ["npm","run","server"]