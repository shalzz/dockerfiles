FROM node:10-alpine AS base
WORKDIR /opt/hsd
RUN apk add --no-cache bash unbound-dev gmp-dev
COPY package.json /opt/hsd

# Install build dependencies and compile.
FROM base AS build
RUN apk add --no-cache g++ gcc make python2 git
RUN npm install --production
RUN npm install imperviousinc/handover

FROM base
# Run time tools
RUN apk add --no-cache bash bind-tools
ENV PATH="${PATH}:/opt/hsd/bin:/opt/hsd/node_modules/.bin"
COPY --from=build /opt/hsd/node_modules /opt/hsd/node_modules/
COPY bin /opt/hsd/bin/
COPY lib /opt/hsd/lib/
ENTRYPOINT ["hsd"]
