FROM node:14 AS BUILD_IMAGE

WORKDIR /app/client

COPY ./ /app/client/


RUN npm install --no-audit && npm prune --production


FROM node:14.18.0-alpine

WORKDIR /app/client

# copy from build image
COPY --from=BUILD_IMAGE /app/client/ /app/client/

RUN npm install --no-audit


CMD ["npm","start","test","lint"]