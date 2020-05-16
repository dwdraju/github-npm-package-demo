FROM node:12-alpine

ARG GITHUB_AUTH_TOKEN
ENV GITHUB_AUTH_TOKEN=$GITHUB_AUTH_TOKEN

RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app

WORKDIR /home/node/app

COPY package.json ./

RUN echo -e "@dwdraju:registry=https://npm.pkg.github.com\n//npm.pkg.github.com/:_authToken=$GITHUB_AUTH_TOKEN" > .npmrc && \
	npm install && \
	rm .npmrc

COPY --chown=node:node . .

CMD npm start
