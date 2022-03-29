ARG NODE_VERSION=17.8-slim

FROM node:${NODE_VERSION}

LABEL "name"="dov-bear-app"

ARG APP_DIR=/app

RUN mkdir ${APP_DIR}
WORKDIR ${APP_DIR} 

#COPY main.js .
#COPY package.json .
#COPY package-lock.json .
#COPY public public
#COPY views views

# Copy file
COPY . .

RUN npm install 

# Run
HEALTHCHECK --interval= --timeout= --start-period=5s --retries=3 \
    CMD curl -s -f http://localhost:${PORT}/healthz > /dev/null || exit 1


ENV PORT=5000
EXPOSE ${PORT}

ENTRYPOINT [ "node", "main.js" ]